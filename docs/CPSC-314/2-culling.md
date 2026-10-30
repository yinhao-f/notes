## Culling vs clipping

## How to decide if an object should be rendered

Bounding boxes:

- sphere
- AABB
- OBB
- convex hull

Tighter bounding boxes are also more costly. Depending on the scene, for static scenes use AABB, for movement use spheres. 

## Point-plane distance

Half plane: everything on one side is inside, everything on the other side is outside. Normal points to inside/outside. 
