

**Run the cgal helper to generate a mesh from obj**

https://github.com/bakpaul/SofaPython3/blob/26_01_add_cgal_example_ugin_python_lib/examples/meshing/CGAL/mesh_from_polyhedron.py

#Download zip here: https://github.com/bakpaul/SofaPython3/tree/26_01_add_cgal_example_ugin_python_lib

`cd ~/Documents/SofaPython3-26_01_add_cgal_example_ugin_python_lib/examples/meshing/CGAL`

Install required packages
```
pip install pandas
pip install vtk
pip install cgal
```

```
python mesh_from_polyhedron.py -i "/home/zhang/Documents/mesh_select/orbital_tissue_down_2.obj" \
                               -o "/home/zhang/Documents/mesh_select/orbitalVol2.vtk" \
                               -c "facet_angle=25 edge_size=4 facet_size=3 facet_distance=0.1 cell_radius_edge_ration=5" \
                               -r "Lloyd"
```

Around 10,000 tetrahedrons would be nice.



**Open different GUI**

`./runSofa /home/chi/Documents/slicersofa_sofa_scratches/test_roi_select.py -g imgui`

`./runSofa /home/chi/Documents/slicersofa_sofa_scratches/test_roi_select.py -g qt`





**Run simulation for ten steps and print out time each step took for debugging**
#export steps
`export SOFA_TIMER_ALL=10`

or shutdown export using:
`export SOFA_TIMER_ALL=0`

#Specify how many steps a sofa scene will run to print out results for n=11 steps
`./runSofa /home/chi/Documents/slicersofa_sofa_scratches/test_roi_select.py -g batch -n 11`

Youngs modulus (pa) calculated from time, mass (SI unit: kg), and size. If in mm, it will be converted to kpa.

Initializing SOFA v25.12 beta version without permanent change sofapython3 paths:
```
cd Documents
```

```
SOFA_ROOT=./SOFA_v25.12.99-full_Linux/SOFA_v25.12.99_Linux \
PYTHONPATH=./SOFA_v25.12.99-full_Linux/SOFA_v25.12.99_Linux/plugins/SofaPython3/lib/python3/site-packages:$PYTHONPATH \
./SOFA_v25.12.99-full_Linux/SOFA_v25.12.99_Linux/bin/runSofa-25.12.99 -l SofaPython3 -g qglviewer \
./slicersofa_sofa_scratches/test_roi_select.py
```

Run on office workstation:\
```
SOFA_ROOT=/home/zhang/Downloads/SOFA_v25.12.99-full_Linux/SOFA_v25.12.99_Linux \
PYTHONPATH=/home/zhang/Downloads/SOFA_v25.12.99-full_Linux/SOFA_v25.12.99_Linux/plugins/SofaPython3/lib/python3/site-packages:$PYTHONPATH \
/home/zhang/Downloads/SOFA_v25.12.99-full_Linux/SOFA_v25.12.99_Linux/bin/runSofa-25.12.99 -l SofaPython3 -g qglviewer \
/home/zhang/Documents/slicersofa_sofa_scratches/test_roi_select.py
```


Problem: previous simulation in OMFS seeks accuracy in model preparation and simulation, but less scalable and reproducible --> became training moduels. Not integrated into routine virtual planning.

Main objective: reproducibility & scalability over absolute accuracey
1. Streamline simulation by integrating Slicer & SOFA for specific-task simulation rather than full surgical process: only simulate a key step for one scene
2. How accurate is acceptable for a specific tasks

Aims
1. Automate mechanical model prep from images for specific tasks.
2. Soft tissue retraction + eyeball position after plate installation
3. plate bending using shell model (easier to validate)
4. Validation using gel phantom and postsurgical images.

Using the gel phantom to validate simulation can be refactored into a separate aim. Add sensors to the scoop to measure the scoop pressure.

Clarify that the purpose is to make the tool available for people to try and do research; no claim about clinical vallidation or clinical use.

Can plate bending be refactored into a separate grant application?



Example of MeshROI select: https://github.com/sofa-framework/sofa/blob/master/examples/Component/Engine/Select/MeshROI.scn

Example of LinearMovementProjectConstraint: /home/chi/SOFA/v25.06.00/share/sofa/examples/Component/Constraint/Projective/LinearMovementProjectiveConstraint.scn
- Export three positions: beginning, under the eye, end of push.
- Interpolation of the tool

Multimaterial model/heterogeneous: https://github.com/sofa-framework/sofa/blob/master/examples/Component/SolidMechanics/FEM/Heterogeneous-TetrahedronFEMForceField.scn

Pieper examples: https://github.com/pieper/SlicerSOFA/blob/main/Experiments/prostate.py
