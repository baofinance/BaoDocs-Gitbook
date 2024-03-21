# Making Changes



## Editor



## Keeping the style consistent

Whatever editor you use you should ensure the style of code isn't changed. The easiest way to do that is to use a formatter that is invoked each time you save changes from a file.

Why? Two main reasons:

1. **People get used to reading code of a certain style so use that style.** Even if your own style was the one used to define the original ten commandments it may not be the style others are used to. The community has developed a standard style and so that is what should be used. It's also the height of disrespect to reformat someone else's masterpiece algorithm to your own style.
2. **If every commit to git has the same style then it's far easier to determine the meaningful code changes** you made, for both you and others reviewing changes, if the style remains the same.\
   If the code you are changing is not in the standard style then checkout the code, reformat it and commit it with a -m"code reformatting to the standard style" comment, to show that there are no syntactic or semantic changes.

Use prettier and set up your editor to format on save
