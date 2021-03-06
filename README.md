# ARCSgeometry
The ARCS Geometry is created using the following output file type.

## Required Packages
The following packages are required to use run this code: airfoil_db, numpy, json, scipy, and shapely. The airfoil_db package can be found [here](https://github.com/usuaero/AirfoilDatabase).

## Running the Code
The code can be run by importing the code and running the main function with a single input of the input formatted JSON file location.

## Input File Format
The input file should have a dictionary with the key "C14". The following keys and corresponding types should be in the "C14" dictionary.

>**"airfoil dat file location" : string**
>>The airfoil dat file to be used for the ARCS geometry. It must be in Selig format, with no text before the airfoil data.
>>
>**"chord [in]" : float**
>>The airfoil chord length in inches.
>>
>**"num arcs" : integer**
>>The number of arcs desired in the geometry. must be greater than or equal to 1.
>>
>**"arc concave" : boolean**
>>Whether to create the arcs concave (true : arcing toward the trailing edge), or convex (false : arcing toward the leading edge).
>>
>**"arc type" : string**
>>Which type of arc to create. The options and corresponding descriptions are:
>>>*"exponential"*
>>>>Create the arcs as having radii inversely increasing from the leading edge toward the trailing edge. The corresponding radius at the hinge point will be equal to the half thickness, with the radius at the trailing edge increasing to infinity.
>>>>
>>>*"reversed_exp"*
>>>>Create the arcs as having radii inversely decreasing from the leading edge toward the trailing edge. The corresponding radius at the hinge point will be at infinity, with the radius at the trailing edge decreasing to the half thickness.
>>>>
>>>*"90%t"*
>>>>Create the arcs as having radii decreasing from the leading edge toward the trailing edge. The corresponding radius at the hinge point will be at nine tenths of the local thickness, with the radius at the trailing edge decreasing to nine tenths of the local thickness.
>>>>
>>>*"hinge_point"*
>>>>Create the arcs as having radii increasing from the leading edge toward the trailing edge. The corresponding arc at each location is centered at the hinge point.
>>>>
>**"section resolution" : integer**
>>The section resolution of the airfoil. This value does not depend on the input airfoil file. A value above 200 is preferable.
>>
>**"shell thickness [mm]" : float**
>>The ARCS geometry skin thickness. A value of 0.8 mm works best for most morphing mechanism applications.
>>
>**"flex start [x/c]" : float**
>>The hinge point in percent chord.
>>
>**"tongue start [in]" : float**
>>The distance ahead of the hinge point where the tongue should begin, in inches. A value of 1 to 2 inches works best for most morphing mechanism applications with a 12 inch chord.
>>
>**"mouth start [in]" : float**
>>The distance ahead of the hinge point where the mouth should begin, in inches. A value of 2 to 3 inches works best for most morphing mechanism applications with a 12 inch chord. This value should always be greater than the "tongue start [in]" value.
>>
>**"TE wall start [x/c]" : float**
>>The wall location in percent chord. Past this location, the parabolic flap will have minimal effect on deflection. Thus, a value closer to 1 is preferable. A value of 0.95 works best for most morphing mechanism applications.
>>
>**"mouth clearance [mm]" : float**
>>The thickness between the tongue and the mouth surfaces. A value of 1.0 mm works best for most morphing mechanism applications with a skin thickness of 0.8 mm.
>>
>**"fillet side length [mm]" : float**
>>The filled side length to be used connecting the hinge point wall to the upper surface. A value of 1.0 mm works best for most morphing mechanism applications with a skin thickness of 0.8 mm.
>>
>**"enthicken" : float**
>>The thickness multiplier to modify the aspect of the airfoil. A value greater than 1 will result in a thicker airfoil, a value less than 1 will result in a thinner airfoil.
>>
>**"skip wing box" : boolean**
>>Whether to skip the wing box geometry during system generation.
>>
>**"show plot" : boolean**
>>Whether to show a plot of the morphing airfoil.
>>
>**"write dxf" : boolean**
>>Whether to write the airfoil shape to a DXF file.
>>
>**"shift to c/4" : boolean**
>>Whether to shift the airfoil so the quarter chord is at the origin.
>>
>**"split return" : boolean**
>>Whether to split off the outer shape for use in generating the files used to model the Horizon aircraft.
>>
>**"guide curve return" : boolean**
>>Whether to split off geometric values concerning the guide curves for use in generating the files used to model the Horizon aircraft.
>>
>**"actuation hole return" : boolean**
>>Whether to split off geometric values concerning the actuation location for use in generating the files used to model the Horizon aircraft.
>>
>**"show legend" : boolean**
>>Whether to show the legend of the parts of the ARCS geometry when plotting.
>>
>**"all black" : boolean**
>>Whether to plot the geometry all in black.
>>
>**"deflection angle [deg]" : float or list**
>>Which deflection angles to examine on the plot. If float given, no deflection will be shown. If a list is given, all deflection values in the list will be plotted on the figure.
>>
>**"deflection type" : string**
>>Which type of deflection to create. The options and corresponding descriptions are:
>>>*"none"*
>>>>Plots no deflection.
>>>>
>>>*"traditional"*
>>>>Plots articulated deflection(s) at the amount(s) specified.
>>>>
>>>*"parabolic"*
>>>>Plots parabolic deflection(s) at the amount(s) specified.
>>>>
>**"hinge at top" : boolean**
>>Whether to locate the hinge point in the middle of the skin on the upper surface. If false, the y-value of the hinge point remains at 0.
>>
>**"dxf file path" : string**
>>The file path where to export the morphing airfoil DXF file (example : "/home/user/Desktop/").
>>
>**"dxf file name" : string**
>>The file name of the exported DXF file (example : "NACA_2412_ARCS").
>>
