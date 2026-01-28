

**Run the cgal helper to generate a mesh from obj**

#Download zip here: https://github.com/bakpaul/SofaPython3/tree/26_01_add_cgal_example_ugin_python_lib

cd ~/Downloads/SofaPython3-26_01_add_cgal_example_ugin_python_lib/examples/CGAL

python mesh_from_polyhedron.py -c "facet_angle=25 edge_size=4 facet_size=3 facet_distance=0.1 cell_radius_edge_ration=5" -r Lloyd



**Open different GUI**

./runSofa /home/chi/Documents/slicersofa_sofa_scratches/test_roi_select.py -g imgui

./runSofa /home/chi/Documents/slicersofa_sofa_scratches/test_roi_select.py -g qt





**Run simulation for ten steps and print out time each step took for debugging**
#export steps
export SOFA_TIMER_ALL=10

#Specify how many steps a sofa scene will run to print out results for n=11 steps
./runSofa /home/chi/Documents/slicersofa_sofa_scratches/test_roi_select.py -g batch -n 11 

