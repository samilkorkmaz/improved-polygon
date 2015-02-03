improved-polygon
================

Polygon class that improves on java.awt.Polygon contains() method.

The contains() method in java.awt.Polygon might not return true for all the points that you expect. Example: xArray = {0, 5, 10, 15, 15, 0}, yArray = {0, 5, 3, 10, 0, 0}. With the standard Polygon class, contains(5,5), contains(15,10), contains(15, 0) will all return false although these points are on the polygon. If you use Matlab's inpolygon function you will get true for all of them.

The reason is related to the "insideness" definition. A point is considered to lie inside a Shape if and only if:
* it lies completely inside the Shape boundary or
* it lies exactly on the Shape boundary and the space immediately adjacent to the point in the increasing X direction is entirely inside the boundary
* or it lies exactly on a horizontal boundary segment and the space immediately adjacent to the point in the increasing Y direction is inside the boundary.

I wrote the class ImprovedPolygon whose contains() method returns true for the above cases by checking if the input coordinates lie on the edges of the polygon using the line formula y = m*x + n and limits of the line end points.
