**Unity WebGL does not directly support the async/await functionality of C#.** 



If you are **not** **using async/await** functionality in your game, **you can skip this page** and move onto the next.



**If you are using async await** operations in your project anywhere, then your **WebGL build might not work** as intended. 

Don't worry, its not a bug in your code.



If you try it on a PC build, it will work fine, just like it was working in your unity editor.



Here is the reason why it might be happening:

- This limitation stems from the fact that WebGL targets a web environment where JavaScript is the primary scripting language, and certain C# features may not translate seamlessly.
- The reason for this lack of support lies in the differences between how JavaScript and C# handle asynchronous operations. 
- While C# offers async/await as a convenient way to work with asynchronous code, JavaScript traditionally uses callback functions and promises.



To overcome this limitation, you can utilize alternative methods for handling asynchronous operations in Unity WebGL, Like using **Coroutines**.



If you convert all your Async Await methods into Coroutines then the WebGL build will work as well!
