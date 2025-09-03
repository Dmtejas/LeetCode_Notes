# Container with most water problem
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.

## Better approach :
* Here, we go with ***Two Pointer*** approach where we take left to beginning of the height array and right to the end of the array and the formula is basically

### Formula - Maximum area = width - (effective height)

And we do this for every element and store the maximum area in ***maxArea*** variable and we return it

* Another thing to keep in mind is that
While incrementing the left we need to check ***height[left] < height[right]*** and vice versa because anyways width is shrinking and the only way that the better area can be constructed if we get a more height on the other side as well 

```java
    public static int maxArea(int[] height) {
        int left = 0;
        int right = height.length - 1;
        int maxArea = 0, currentArea = 0;

        while(left < right) {
            currentArea = (Integer.min(height[left], height[right]) * (right - left));
            System.out.println(currentArea);
            if(maxArea < currentArea) {
                maxArea = currentArea;
            }
            if(height[left] < height[right]) {
                left++;
            } else if(height[left] >= height[right]) {
                right--;
            }
        }
        return maxArea;
    }

```