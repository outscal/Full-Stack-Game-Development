# Chapter 27 - Solution for chapter 26 - MAT II - MineSweeper Clone

**[Rules]**

- The board is divided into cells, with mines randomly distributed.
- To win, you need to open all the cells.
- The number on a cell shows the number of mines adjacent to it. Using this information, you can determine cells that are safe, and cells that contain mines.
- Interact, evolve and enjoy!

**[Task]**

- Create a board of any size n * n, such that n ≥ 9.
- You should take two integers x and y (where the player want to click) as input from the user(player).
- Remember whatever the first input is given by the user that place should not contain the mine i.e. generate the board and number on the board after taking the first input.
- After each input shows the updated status of the board and asks the user to input the next step.
- The game should run until either player loses the game or wins the game.

<details>
<summary>main.cpp</summary>
<p>

```cpp
#include "Game.h"

int main()
{
	Minesweeper::Game newGame;
	newGame.Run();
}
```

</p>
</details>
<br>
<details>
<summary>input.h</summary>
<p>

```cpp
#pragma once
namespace Minesweeper
{
	struct Vector
	{
		int x;
		int y;

		bool operator == (Vector const &vector)
		{
			if(x == vector.x && y == vector.y)
				return true;
			return false;
		}
	};

	struct Input
	{
		Vector index;
		bool isMark;
	};
}
```

</p>
</details>
<br>
<details>
<summary>Game.h</summary>
<p>

```cpp
#pragma once
#include <iostream>
#include "Input.h"
#include "Board.h"

namespace Minesweeper
{
	class Game
	{
	private:
		//Variables
		Input m_Input;
		Board m_Board;
		//Functions
		void GetInput();
		bool IsInputValid();
		void ProcessInput();
		bool IsGameOver();

	public:
		// Constructor and destructor
		Game();
		virtual ~Game();

		//Game Loop
		void Run();
	};
}
```

</p>
</details>
<br>
<details>
<summary>Game.cpp</summary>
<p>

```cpp
#include "Game.h"
namespace Minesweeper
{
	// Constructor and destructor
	Game::Game(){}
	Game::~Game(){}

	//Functions
	void Game::GetInput()
	{
		std::cout << "Enter Row Index, Column Index, reveal(0)/Mark(1) :\n";
		std::cin >> m_Input.index.y >> m_Input.index.x >> m_Input.isMark;
	}
	bool Game::IsInputValid()
	{
		system("cls");
		if (!m_Board.IsInBounds(m_Input.index))
		{
			std::cout << "Invalid Input. Retry!\n";
			return false;
		}
		return true;
	}
	void Game::ProcessInput()
	{
		m_Board.Process(m_Input);
	}
	bool Game::IsGameOver()
	{
		if (m_Board.IsGameOver())
		{
			std::cout << "\n" 
				<< (m_Board.IsGameWon() ? "WIN" : "LOSE") 
				<< " !!!\n\n";
			m_Board.DisplayBoard();
			return true;
		}
		return false;
	}

	//Game Loop
	void Game::Run()
	{
		do
		{
			m_Board.DisplayBoard();
			GetInput();
			if (!IsInputValid())
				continue;
			ProcessInput();
		} while (!IsGameOver());
	}
}
```

</p>
</details>
<br>
<details>
<summary>Tile.h</summary>
<p>

```cpp
#pragma once
#include <iostream>

namespace Minesweeper
{
	enum class TileState
	{
		Hidden = 0,
		Revealed = 1,
		Marked = 2
	};

	enum class TileType
	{
		Empty = 0,
		Bomb = 1,
		Count = 2
	};

	class Tile
	{
	private:
		// Variables
		TileState m_State;
		TileType m_Type;

		int m_AdjacentBombCount;

		//Functions
		void DisplayRevealed();
	public:
		// Constructor and destructor
		Tile();
		virtual ~Tile();

		void Display();
		bool IsState(TileState);
		void SetState(TileState);
		bool IsType(TileType);
		void SetBomb();
		void SetBombCount(int);
	};
}
```

</p>
</details>
<br>
<details>
<summary>Tile.cpp</summary>
<p>

```cpp
#include "Tile.h"
namespace Minesweeper
{
	Tile::Tile()
	{
		m_State = TileState::Hidden;
		m_Type = TileType::Empty;
		m_AdjacentBombCount = -1;
	}
	Tile::~Tile()
	{
	}
	void Tile::Display()
	{
		switch (m_State)
		{
		case TileState::Hidden:
			std::cout << "#";
			break;
		case TileState::Marked:
			std::cout << "O";
			break;
		default:
			DisplayRevealed();
			break;
		}
	}
	void Tile::DisplayRevealed()
	{
		switch (m_Type)
		{
		case TileType::Bomb:
			std::cout << "X";
			break;
		case TileType::Count:
			std::cout << m_AdjacentBombCount;
			break;
		default:
			std::cout << " ";
			break;
		}
	}

	bool Tile::IsState(TileState checkState)
	{
		return m_State == checkState;
	}
	void Tile::SetState(TileState  newState)
	{
		m_State = newState;
	}
	bool Tile::IsType(TileType type)
	{
		return m_Type == type;
	}
	void Tile::SetBomb()
	{
		m_Type = TileType::Bomb;
	}
	void Tile::SetBombCount(int count)
	{
		if (count == 0)
		{
			m_Type = TileType::Empty;
			return;
		}
		m_Type = TileType::Count;
		m_AdjacentBombCount = count;
	}
}
```

</p>
</details>
<br>
<details>
<summary>Board.h</summary>
<p>

```cpp
#pragma once
#include "Input.h"
#include "Tile.h"

namespace Minesweeper
{
	class Board
	{
	private:
		//Variables
		Vector m_MaxSize;
		Tile** m_Tiles;
		
		int m_BombCount;
		bool b_IsBombPlaced;

		bool b_IsGameOver;
		bool b_IsGameWin;

		int m_UnrevealedCount;
		//Functions
		void InitTiles();
		void DestroyTiles();
		// Checking
		bool CheckProcessAvailable(Input);
		bool CheckState(Vector, TileState);
		bool CheckType(Vector, TileType);
		//GamePlay
		void ProcessMarking(Vector);
		void ProcessReveal(Vector);
		void PlaceBombs(Vector);
		void SetAllAdjacentBombCount();
		int CaculateAdjacentBomb(Vector);
		Vector GetRandomPosition();
		void FloodFill(Vector);
	public:
		// Constructor and destructor
		Board();
		virtual ~Board();
		// Checking 
		bool IsInBounds(Vector);
		bool IsGameOver();
		bool IsGameWon();
		// gameplay
		void Process(Input);
		//Display
		void DisplayBoard();
	};
}
```


</p>
</details>
<br>
<details>
<summary>board.cpp</summary>
<p>

```cpp
#include "Board.h"

namespace Minesweeper
{
	void Board::InitTiles()
	{
		m_Tiles = new Tile*[m_MaxSize.x]();
		for (int x = 0; x < m_MaxSize.x; x++)
			m_Tiles[x] = new Tile[m_MaxSize.y];
	}
	void Board::DestroyTiles()
	{
		if (m_Tiles == NULL)
			return;

		for (int y = 0; y < m_MaxSize.y; y++)
			delete[] m_Tiles[y];
		delete[] m_Tiles;
	}
	Board::Board()
	{
		m_MaxSize.x = 9;
		m_MaxSize.y = 9;
		m_BombCount = 10;
		b_IsBombPlaced = false;
		b_IsGameOver = false;
		b_IsGameWin = false;
		m_UnrevealedCount = (m_MaxSize.x * m_MaxSize.y);
		InitTiles();
	}
	Board::~Board()
	{
		DestroyTiles();
	}
	// Checking 
	bool Board::IsInBounds(Vector position)
	{
		return position.x >= 0 && 
			position.x < m_MaxSize.x && 
			position.y >= 0 && 
			position.y < m_MaxSize.y;
	}
	bool Board::IsGameOver()
	{
		if (m_UnrevealedCount == m_BombCount)
		{
			b_IsGameOver = true;
			b_IsGameWin = true;
		}
		return b_IsGameOver;
	}
	bool Board::IsGameWon()
	{
		return b_IsGameWin;
	}
	bool Board::CheckProcessAvailable(Input input)
	{
		Vector pos = input.index;
		if (CheckState(pos,TileState::Revealed))
		{
			std::cout << "Already revealed\n";
			return false;
		}
		// to check if the request is to reveal a marked tile
		if (!input.isMark && CheckState(pos, TileState::Marked))
		{
			std::cout << "Marked Tile\n";
			return false;
		}
		return true;
	}
	bool Board::CheckState(Vector pos, TileState state)
	{
		return m_Tiles[pos.x][pos.y].IsState(state);
	}
	bool Board::CheckType(Vector pos, TileType type)
	{
		return m_Tiles[pos.x][pos.y].IsType(type);
	}

	//Gameplay
	void Board::Process(Input input)
	{
		if (!CheckProcessAvailable(input))
		{
			std::cout << "Process Not Possible\n";
			return;
		}

		if (input.isMark)
		{
			ProcessMarking(input.index);
			return;
		}
		ProcessReveal(input.index);
	}
	void Board::ProcessMarking(Vector pos)
	{
		if (CheckState(pos, TileState::Marked))
			m_Tiles[pos.x][pos.y].SetState(TileState::Hidden);
		else
			m_Tiles[pos.x][pos.y].SetState(TileState::Marked);
	}
	void Board::ProcessReveal(Vector pos)
	{
		m_Tiles[pos.x][pos.y].SetState(TileState::Revealed);
		m_UnrevealedCount--;
		if (!b_IsBombPlaced)
		{
			PlaceBombs(pos);
			SetAllAdjacentBombCount();
		}
		if (CheckType(pos, TileType::Empty))
			FloodFill(pos);
		
		if (CheckType(pos, TileType::Bomb))
		{
			b_IsGameOver = true;
			b_IsGameWin = false;
		}

	}
	void Board::PlaceBombs(Vector firstPos)
	{
		srand(time(0));
		Vector randomPos = firstPos;
		for (int i = 0; i < m_BombCount; i++)
		{
			while (randomPos == firstPos || CheckType(randomPos,TileType::Bomb))
				randomPos = GetRandomPosition();

			m_Tiles[randomPos.x][randomPos.y].SetBomb();
		}
		b_IsBombPlaced = true;
	}
	void Board::SetAllAdjacentBombCount()
	{
		Vector current;
		for (int x = 0; x < m_MaxSize.x; x++)
		{
			for (int y = 0; y < m_MaxSize.y; y++)
			{
				current.x = x;
				current.y = y;
				if (!CheckType(current, TileType::Bomb))
					m_Tiles[x][y].SetBombCount(CaculateAdjacentBomb(current));
			}
		}
	}
	int Board::CaculateAdjacentBomb(Vector pos)
	{
		Vector index;
		int count = 0;
		for (int i = -1; i <= 1; ++i)
		{
			for (int j = -1; j <= 1; ++j)
			{
				index.x = pos.x + i;
				index.y = pos.y + j;
				if (IsInBounds(index))
				{
					if (CheckType(index,TileType::Bomb))
						count++;
				}
			}
		}
		return count;
	}
	Vector Board::GetRandomPosition()
	{
		Vector randompos;
		randompos.x = rand() % m_MaxSize.x;
		randompos.y = rand() % m_MaxSize.y;
		return randompos;
	}

	void Board::FloodFill(Vector pos)
	{
		Vector index;
		for (int i = -1; i <= 1; ++i)
		{
			for (int j = -1; j <= 1; ++j)
			{
				index.x = pos.x + i;
				index.y = pos.y + j;
				if (!IsInBounds(index))
					continue;

				if (CheckState(index, TileState::Revealed))
					continue;

				m_Tiles[index.x][index.y].SetState(TileState::Revealed);
				m_UnrevealedCount--;
				if(CheckType(index,TileType::Empty))
					FloodFill(index);
			}
		}
	}

	//Display
	void Board::DisplayBoard()
	{
		std::cout << " |";
		for (int x = 0; x < m_MaxSize.x; x++)
			std::cout << x << "|";
		std::cout << "\n";
		for (int y = 0; y < m_MaxSize.y; y++)
		{
			std::cout << y << "|";
			for (int x = 0; x < m_MaxSize.x; x++)
			{		
				m_Tiles[x][y].Display();
				std::cout << "|";
			}
			std::cout << "\n";
		}
		std::cout << "\n";
		std::cout << "Unrevealed : " << m_UnrevealedCount << "\n";
		std::cout << "Bombs : " << m_BombCount << "\n";
	}
}
```

</p>
</details>
<br>













