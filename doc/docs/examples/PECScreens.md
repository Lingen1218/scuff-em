# Casimir forces between infinitely extended silicon 
  beams (1D periodicity)

The files for this example may be found in the
`share/scuff-em/examples/SiliconBeams` subdirectory
of your **scuff-em** installation.

## **GMSH** geometry file for the unit-cell geometry
   of a single beam: 
   [`RoundedBeamUnitCell.geo`][RoundedBeamUnitCellGeo]

This geometry file describes only the portion of a
single cylinder that lies within the *unit cell,*
i.e. the cell that will be infinitely periodically
replicated. To produce a discretized surface-mesh
representation of this geometry, we run it through 
**GMSH:** 

````bash
% gmsh -2 RoundedBeamUnitCell.geo
````
This produces the file `RoundedBeamUnitCell.msh`, which
I rename to `RoundedBeamUnitCell_192.msh` to indicate
the number of interior edges (this information may be 
found, for example, by running 
`scuff-analyze --mesh RoundedBeamUnitCell.msh`).
You can open the `.msh` file in **gmsh** to visualize
the unit-cell mesh.

Note the following:

 * For 1D periodic geometries in **scuff-em**, the direction
   of infinite extent must be the *x* direction.

 * Only the sidewall of the cylinder is meshed;
   the endcaps must not be meshed.

 * For surfaces that straddle the unit-cell boundaries
   (as is the case here, each triangle edge that lies
   on the unit-cell boundary must have an identical
   image edge on the opposite side of the unit cell.

 * In this case the unit cell is 1 $\mu$m long.
   More generally the unit cell could have any length.

## **scuff-em** geometry file for two infinitely
   extended silicon cylinders:
   [`RoundedBeams_192.scuffgeo`][RoundedBeamsScuffgeo]

The **scuff-em** geometry file describes a 1D
periodic geometry consisting of a unit cell that is
periodically replicated every 1 $\mu$m. (The length
of the lattice vector specified by the `LATTICE`
statement here should agree with the length of 
the unit cell as defined in the **GMSH** geometry
file.) The unit cell

[RoundedBeamUnitCellGeo]: examples/CasimirCylinders/RoundedBeamUnitCell.geo
[RoundedBeamsScuffgeo]: examples/CasimirCylinders/RoundedBeams_192.scuffgeo
[id2]: /path/to/image "alt text"
