Question Link: [https://leetcode.com/problems/circle-and-rectangle-overlapping/](https://leetcode.com/problems/circle-and-rectangle-overlapping/)

```cpp
class Solution {
    bool isInside(int x, int y, int xc, int yc, int r) {
        //equation of circle
        return (x - xc) * (x - xc) + (y - yc) * (y - yc) <= r * r;
    }
public:
    bool checkOverlap(int r, int xc, int yc, int x1, int y1, int x2, int y2) {
        // check whether the circle is within the rectangle
        if (x1 <= xc && xc <= x2 && y1 <= yc && yc <= y2)
            return true;
        
        // check whether any point on the ractanble border is within the circle
        // limit the border scan within the circle radius:
        // x = max(x1, xc - r); x <= min(x2, xc + r)
        // y = max(y1, yc - r); y <= min(y2, yc + r)
        for (auto x = max(x1, xc - r); x <= min(x2, xc + r); ++x) {
            if (isInside(x, y1, xc, yc, r) || isInside(x, y2, xc, yc, r))
                return true;
        }
        for (auto y = max(y1, yc - r); y <= min(y2, yc + r); ++y) {
            if (isInside(x1, y, xc, yc, r) || isInside(x2, y, xc, yc, r))
                return true;                             
        }
        return false;
    }
};
```
