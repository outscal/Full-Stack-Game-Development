<style>
@import url(https://fonts.googleapis.com/css?family=Open+Sans:400);
:root{
  --subHeadingFontSize:1.5rem;
  --blockContentFontSize:1rem;
  --blockTextColor:#555555;
  --blockBackgroundColor:#EDEDED;
}
blockquote{
  font-size: var(--blockContentFontSize);
  width:90%;
  color: var(--blockTextColor);
  padding-bottom:0.1rem;
  padding-top:0.5rem;
  margin-top:0.5rem;
  line-height:1.6;
  position: relative;
  background:var(--blockBackgroundColor);
}
.task, .submission{
  font-style: normal;
  font-weight: bold;
  font-size:var(--subHeadingFontSize);
  font-family:Arial;
}
.task::before{
  content: "📝";
}
.submission::before{
  content: "✅";
}


blockquote::after{
  content: '';
}
figure{
  text-align:center;
}
figure img{
  width: 70%;
}
figcaption{
  font-weight: bold;
  text-decoration: underline;
}

</style>



<div style="margin: auto 5%">

<div style = "text-align: center">
<h1><strong>Assignment 2 - Creating Animations (Idle)</strong></h1>
</div>
<span class="task">[Task] Make an idle animation</span>

<blockquote>
<ul>
<li>Fork the repository given below.<br>🔗Link: <a href="https://github.com/outscal/2D-Platformer-Game"><strong><em>Github Repo</em></strong></a></li>
<li>After the fork, clone the repository and start building your 2D platformer game.</li>
</ul>
</blockquote>


<br>
<figure>
<img src ="https://media.tenor.com/podEhEbjoSYAAAAC/haminations.gif"  >
<figcaption> Idle Animation</figcaption>
</figure>

<span class = "submission">[Submission]</span>
<blockquote>
<ul>
<li>Create a new Branch named Feature1-Animations.</li>
<li>Put your code there and make a pull request to your own repository, not the Outscal one.
</li>
<li>Share the pull request as a submission link.</ul>
</blockquote>
</div>