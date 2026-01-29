

**Run the cgal helper to generate a mesh from obj**

#Download zip here: https://github.com/bakpaul/SofaPython3/tree/26_01_add_cgal_example_ugin_python_lib

`cd ~/Downloads/SofaPython3-26_01_add_cgal_example_ugin_python_lib/examples/CGAL`

`python mesh_from_polyhedron.py -c "facet_angle=25 edge_size=4 facet_size=3 facet_distance=0.1 cell_radius_edge_ration=5" -r Lloyd`



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

Initializing SOFA beta version without permanent change sofapython3 paths:
```
SOFA_ROOT=/home/chi/Downloads/SOFA_v25.12.99-full_Linux/SOFA_v25.12.99_Linux \
PYTHONPATH=/home/chi/Downloads/SOFA_v25.12.99-full_Linux/SOFA_v25.12.99_Linux/plugins/SofaPython3/lib/python3/site-packages:$PYTHONPATH \
/home/chi/Downloads/SOFA_v25.12.99-full_Linux/SOFA_v25.12.99_Linux/bin/runSofa-25.12.99 -l SofaPython3 -g qglviewer \
/home/chi/Documents/slicersofa_sofa_scratches/test_roi_select.py
```



Problem: previous simulation in OMFS seeks accuracy in model preparation and simulation, but less scalable and reproducible --> became training moduels. Not integrated into routine virtual planning.

Main objective: reproducibility & scalability over absolute accuracey
1. Streamline simulation by integrating Slicer & SOFA for specific-task simulation rather than full surgical process: only simulate a key step for one scene
2. How accurate is acceptable for a specific tasks

Aim 1: Automate mechanical model prep from images for specific tasks.
Aim 2: Soft tissue retraction + eyeball position after plate installation
Aim 3: plate bending using shell model (easier to validate)
Aim 4: validation using gel phantom and postsurgical images.



