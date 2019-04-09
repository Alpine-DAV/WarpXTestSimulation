Contouring (with Contour Tree) Example for WarpX
================================================

## MacOS
Run with

```
mpirun -np 1 ../WarpX/Bin/main3d.llvm.TPROF.MPI.OMP.ex inputs.3d
```

## Cori
  * Apply for interactive job on compute node
```
salloc -N 1 -C haswell -t 00:30:00 --account=m3090

  * Once compute node is available, run with
```
srun ../WarpX/Bin/main3d.gnu.haswell.TPROF.MPI.OMP.ex inputs.3d
```

## Configuration
In situ analysis startes in time step 100 and runs every time step. To changes this behavior, change ``insitu.start`` and ``insitu.int`` in ``inputs.3d``.

## Output
To change in situ analysis, link to the corresponding Ascent script.
  * ``rm ascent_actions.json; ln -s ascent_actions_threshold.json ascent_actions.json``: Thresholding to ``threshold_nnnn.png``
  * ``rm ascent_actions.json; ln -s ascent_actions_threshold.json ascent_actions.json``: Contouring with 15 levels  to ``levels_nnnn.png``
  * ``ascent_actions_smartisosurf.json``: Does not work, yet. Requires custom Ascent install.

**IMPORTANT**: Currenly supports only running with a single rank as input deck forces single box/block.

