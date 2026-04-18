To integrate the **Replay Service** with your current code, let's first understand how the player will be interacting with the replay mechanic and according to that flow we will start implementing our code.



Right now when a Battle ends, you can see a **Game End UI Screen** which currently has a Home button on it. Here we want a replay button as well in the UI upon pressing which the battle we replayed once again without any player input.



![](https://outscal-assets.s3.ap-south-1.amazonaws.com/production/LMS/634ff2a63bfd3eecf3cfe038/11_01_2023__13_45_31.png)



To add a replay button, open the script `**GameEndView.cs**` :

- Add a `serializeField` named `replayButton`
- Subscribe a method in UI Controller for the button click event

```javascript
public class BattleEndUIView : MonoBehaviour, IUIView
{
		[SerializeField] private Button replayButton;
		
		private void SubscribeToButtonClicks()
		{
    		replayButton.onClick.AddListener(controller.OnReplayButtonClicked);
    		homeButton.onClick.AddListener(controller.OnHomeButtonClicked);
		}
}
```



In your `**BattleEndUIController.cs**` you need to define a method called `**OnReplayButtonClicked()**` that you are subscribing.

Here is what this function will do:

- Set Replay State as Active
- Set Input State as Inactive
- Invoke an event called **OnReplayButtonClicked** in Event Service

```javascript
public void OnReplayButtonClicked()
{
    GameService.Instance.ReplayService.SetReplayState(Replay.ReplayState.ACTIVE);
    GameService.Instance.InputService.SetInputState(Input.InputState.INACTIVE);
    GameService.Instance.EventService.OnReplayButtonClicked.InvokeEvent();
}
```

You will need to create this event as well. So open you `**EventService.cs**` and create another `GameEventController` with the same name. 



When this event is invoked, there are 3 things that will occur:

- Game End UI will be disabled
- Battle Service will reload the the recently played battle
- Command Invoker will set the replay stack inside Replay Service



## 1) Battle Service will reload the the recently played battle


---

```javascript
private void SubscribeToEvents()
{
    GameService.Instance.EventService.OnBattleSelected.AddListener(LoadBattle);
    GameService.Instance.EventService.OnReplayButtonClicked.AddListener(ReplayBattle);
}

private void ReplayBattle() => LoadBattle(currentBattleId);
```



## 2) Command Invoker will set the replay stack inside Replay Service


---

```javascript
public CommandInvoker() => SubscribeToEvents();

private void SubscribeToEvents() => GameService.Instance.EventService.OnReplayButtonClicked.AddListener(SetReplayStack);

public void SetReplayStack()
{
    GameService.Instance.ReplayService.SetCommandStack(commandRegistry);
    commandRegistry.Clear();
}
```



## 3) Game End UI and action selection UI will be disabled


---

```javascript
public void Init(int battleCount)
{
    ShowBattleSelectionView(battleCount);
    SubscribeToEvents();
}

private void SubscribeToEvents() => GameService.Instance.EventService.OnReplayButtonClicked.AddListener(HideBattleEndUI);

public void HideBattleEndUI() => battleEndController.Hide();

public void ShowActionSelectionView(List<CommandType> executableActions)
{
    switch (GameService.Instance.ReplayService.ReplayState)
    {
        case Replay.ReplayState.ACTIVE:
            GameService.Instance.ReplayService.ExecuteNext();
            break;
        case Replay.ReplayState.DEACTIVE:
            actionSelectionController.Show(executableActions);
            GameService.Instance.InputService.SetInputState(InputState.SELECTING_ACTION);
            break;
    }
}
```



That's all you need to do to replay your game again, and you can replay it multiple times if you wish to. 

Its that easy to implement a replay functionality if you know how to utilize Command Pattern in your code.




<iframe src="https://www.loom.com/embed/8c4ce323dc7d40b8a73eb583a075bcee" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





**Time to sit back and watch your game!!**



![](https://tenor.com/view/replay-instant-replay-gif-24027882.gif)
