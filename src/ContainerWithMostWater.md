# Container with most water problem
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.

## Better approach :
* Here, we go with ***Two Pointer*** approach where we take left to beginning of the height array and right to the end of the array and the formula is basically

### Formula - Maximum area = width - (effective height)

And we do this for every element and store the maximum area in ***maxArea*** variable and we return it 