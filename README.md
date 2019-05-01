nut_knob

What:

	A parametric model of a knob for tool free adjustment of nuts and hex head bolts.
	Based on the tutorial: 
	(29) FreeCAD 0 .17 Tutorial : . Design a Knob using Part Design - YouTube
	https://www.youtube.com/watch?v=rgstQi9jpGc
	
	More info on this below.

Status:
	Printed, seem to work well, lets see in a year.
	
Some documentation for the Model Tree:


ss				spread sheet with some important and and modifiable dimensions

b_knob 			body for the knob, without fillets -- body all done in part design

	s_master_dims		sketch with some drawing with dimensions used as external geometry for other sketches
						these are all ( probably ) based on the spreadsheet ss


p_base_cyl				pad: a cylinder we "cut" the knob from
   s_outter_radius      sketch for above 
   
dp_knob_upper_face		datum plane: I think i attach sketches to it for the flutes


p_bolt_shaft			pocket: for the bolts shaft

p_flutes				pocket: first pocket for the flutes to make the circular cross section parts


p_straighten_flutes		pocket: second pocket for the flutes to straighten them out


PollarPatern			takes the straighten flutes ( one arm only ) and propagates them around the knob

p_bottom_relief			pocket: gives relief so arms of knob do not touch 


p_final_parametric_model   pocket: this is as far as I could go with parametric model, I cannot get fillets to work on this sucker 

	s_hex_insert		sketch: insert for nut or hex hear


Fillet  				fillet of refined part below, this is not parametric but is the basis for a mesh and stl export
	grass_collect_v1    (part workbench) refinement of p_final_parametric_model it appears to be some sort of copy without links to p_final... so is not parametric
						but I can ( part workbench ) fillet it
						
Fillet001				same as Fillet but with different dimensions, see info below for different dimensions
..... more fillets	


Info on fillets ( names in the refined parts ) 

for 1/4 nut nut
one_quarter_v1


	shaft radius             3.15  printed too tight   try 3.25
	nut_point_radius         6.30  printed too tight   try  6.4
	nut_depth                5.00  may be just enough  try 5.0
	knob_outer_radius		21.00
	knob_inner_radius		10.00
	
one_quarter_v2

	shaft radius             3.25  easy to thread in, seems same as above,   
	nut_point_radius         6.4   still too tight, say another .2 for next
	nut_depth                5.00  may be just enough  try 5.0  adjusted knob height, so ss does not match this
	knob_outer_radius		21.00
	knob_inner_radius		10.00	
	knob height of 15 + 5 may be more than needed, try 10
	
one_quarter_v3   this seems to work 

	shaft radius             3.35   still pretty tight 
	nut_point_radius         6.6    
	nut_depth                5.00   add a mm or two
	knob_outer_radius		21.00
	knob_inner_radius		10.00	
	knob_height at flutes   10 mm  
	
	printed
	     30% on c clone printer top side down 
	
	
 
grass collector lowest bolt hold one
grass_collect_v1

	shaft radius             3.85  printed too tight   try 4.00
	nut_point_radius         7.2   printed too tight   try 7.5
	nut_depth                5.00  add 1 mm 
	knob_outer_radius		21.00
	knob_inner_radius		10.00

grass_collect_v2

	shaft radius              4.00
	nut_point_radius         7.5
	nut_depth                6.00   
	knob_outer_radius		21.00
	knob_inner_radius		10.00
    knob_height at flutes   10 mm  
	
	
	
------------------ knob tutorial  --------------------


(29) FreeCAD 0 .17 Tutorial : . Design a Knob using Part Design - YouTube
https://www.youtube.com/watch?v=rgstQi9jpGc


I originally followed the tutorial, except that I skipped the material saving
cutout in each flute.

Then I added a spreadsheet to control some of the dimensions of the
design.

I also did some renames of sketches..... to make it easier to understand the model.

The spreadsheet seemed to interfere with the chamfers of the object.
I was never able to get these to work again.  I came up with a sort of work around:

Use the part workbench to refine the un-chamfered model.  This creates a new object
in the model which does not seem to be parametric with the model:  It does not update
when you update the base features from which it was created.  But using the part workbench
you can in one step chamfer all the edges.  


So the work-flow to make a new knob with different dimensions is:

*  Check to make sure there is not already a refined part with the desired dimensions.
   If there is just mesh and export stl.
*  If not: Change the spreadsheet to the desired dimensions.
*  Refine the model, create a new refined part.
*  Chamfer the refined part.
*  Mesh and export the stl.


...... to do .........

would be nice to have a table of dimensions of different fasteners 
to use in customizing the model.

find a better way to chamfer the model.

...... about ( my version of )freeCad .......
 
OS: Windows 10
Word size of OS: 64-bit
Word size of FreeCAD: 64-bit
Version: 0.18.15959 (Git)
Build type: Release
Branch: master
Hash: 397418078a6f61e8c39cedfe1160adc2abd73510
Python version: 2.7.14
Qt version: 4.8.7
Coin version: 4.0.0a
OCC version: 7.2.0
Locale: English/UnitedStates (en_US)


