An example mpcdi with fisheye info, and point-of-view renderings.

NOTE: for the fisheye renders, only the _vertices_ were fisheye-mapped, the connecting edge-lines were not curved.
ie the points are in the right place, but in a proper render, the lines would be slightly curved.

Projector 1 (lower right) is the hardest condition - it is a fisheye and also an anamorphic lens.  (There is no skew to the anamorphism however, so I guess it could be harder.  In practice, we haven't actually seen noticeable skew...). Projector 5 (listed below) might be easier to start with.

Projector 2 (top left) is anamorphic (stretching vertically).  But not fisheye.

Projector 5 (center back) is facing directly at the wolfhead - default orientation.  It is fisheye. Not anamorphic.

Projector 6 (center front) is also facing directly at the wolfhead.  But is planar.  (5 and 6 should result in similar POVs, but with 5 showing the fisheye nature of the render).
