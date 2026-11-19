## Culling vs clipping

## Culling vs clipping

- culling: throws away an object entirely
    - reduce computation load
    - optimization, not a must
- clipping: trims part of an object that's out of the view frustum
    - simplifies rasterization
    - for correctness

## Bounding volume

- sphere
- AABB - axis aligned bounding box
- OBB - oriented bounding box
- 8-DOP - 8-sided discrete orientation polytope
- convex hull

### Bounding volume hierarchy (BVH)

```
test(node):
    check node.volume against frustum
    if outside:
        discard the subtree and return
    if inside:
        draw subtree
    if intersect:
        draw leaf or recurse onto children
```


## View volume culling

## View volume clipping

## Backface culling

## occlusion culling

## Point-plane distance

Half plane: everything on one side is inside, everything on the other side is outside. Normal points to inside/outside. 
