# Modded Triple Z Mod Arms

This mod builds uppon [PBSuper's great work on the kinematic triple z for the VZTrident][1]. While the basics still the same, I changed parts and adapted it to be easier to source, mainly removing difficult to find magnets and metal balls. 

All the information from PBSuper works still valid and you will need to read and understand both to know what to do. **Because of that I rate this as a hard/non trivial mod.**

Also removed some cosmetic stuff that made it more annoying to print for the sake of looking better, since I don't really care about how a 3d printer looks.

## Parts needed, that are different from PBSuper's:

|Quantity|Part|Link|Extra info|
|:------:|----|----|----------|
|3|10mm threaded ball|[Mandala Roseworks][2]||
|3|M3 screw||Long enough to hold the bed at the needed height. For an AWD 330 I used M3x35.
|3|Spacer|[McMaster Carr example][3]|Most hardware stores will sell aluminum spacers on different heights, make sure to get one that matches the height you need. Get the unthreaded ones with enough clearance for the M3 screw (even if it's not metric, doesn't matter really since they are unthreaded).
|3|20x10x5 Magnets|[Amazon US][4]|Anything that is 20x10 will work.||
|6|M3x30 Dowel|[Amazon US][5]|Can also be found on hardware stores/McMaster. Unfortunately because *math* it does need to be metric and exactly 3mm.
|3|M3 inserts||For the cable chain holding part on the back arm.

## Parts you already have it or may want to use


|Quantity|Part|Link|Extra info|
|:------:|----|----|----------|
|3|Oldham Coupler||Not needed on the miraculous chance a lead screw is perfect straight. It's kind of a pain to screw them on the back arm.
|3|Lead screw nut||No need to be anti-backlash, but POM seems to be the best choice atm.

## Printed parts

Aside from the parts on this directory, you will need also to find the motor/MGN Rail combination for your specific case out on PBSuper's work or discord server's mod channel.

The arms here have the screw spacing for *MGN12C* blocks. Adapting it to *MGN12H* should be trivial and the STEP files are available for that.

|Quantity|Part|Extra info|
|:------:|----|----------|
|1|Left arm|
|1|Right arm|It's a mirrored left arm.
|1|Back arm|You may want to mirror it depending on what side you want the cable chain.
|3|Magnet Block|This is used to hold the magnet in place.

## Printing and Assembling

The orientation on the STL files should be correct. In case it's not, print with the flat face with the logo down. After printing you may want to do some checking on the tolerances for screw heads on the holes that will be used to attach to the MGN rail, and also do some cleanup with a 3mm drill bit on the dowel pin holes.

Assembling is pretty straighforward:

1. Insert the dowels on the respective holes and make sure they go all the way back
2. Put the magnet on the slot, and make sure it is centered/ish in case it's smaller
3. Use the *magnet block* to push the magnet up until it's firmly set against the dowels. The blocks are kinda tight, so you may want to file/sand a bit to make it easier to set it. 
4. If you want extra holding, you can add some heat inserts on the sides of the arm and use a screw to hold the magnet block. In my experience, the blocks are snug enough that I don't need that.

It will look kinda like this:

![Inspection view][10]

![Front view][11]

![Assembled with spacers][12]

The long spacers in this case is to clear the AWD motors in the front. They wull probably be smaller if AWD isn't a problem.

After that, the instructions and everything else should follow PBsuper's mod since there are no more changes.

## Just for the fun of it: *MATH* (for nerds)

In case you want to use different size balls or alter that part in any way, this is the basic idea, considering 3mm dowels and a 10mm ball.

![Ball contact drawing][6]

The important part in this case, is the contact between steel ball and dowels:

>Furthermore, for balanced stiffness in all directions, the contact force vectors should intersect the plane of coupling action at an angle of 45&deg;  
<cite>&mdash; (Slocum, A. H. (Design of three-groove kinematic couplings [(1992)][8])</cite>

So since what we have there is a right triangle, the distance between dowel centers in relation to the ball diameter is given by the hypotenuse for the triangle formed between the three circle centers: $d = \sqrt{a^2+b^2}$ and since both sides are equal we have $d = \sqrt{2 \cdot s^2}$ where $s$ is the side/distance between dowel and ball centers, and since we can calculate that with $d = \sqrt{2\cdot(\frac{bd}{2}+\frac{dd}{2})^2}$ 
where $bd$ and $dd$ are, respectively, *ball diameter* and *dowel diameter*. In the case of 10mm balls and 3mm dowels: 

$d = \sqrt{2\cdot(\frac{10}{2}+\frac{3}{2})^2} \Rightarrow d= \sqrt{2\cdot(6.5)^2} \Rightarrow d = \sqrt{84.5} \Rightarrow d = 9.19238$

So in case anyone wants to create a different mount size, that solves the distance between dowels problem. 

Changing the distance **between arms**, as it would be needed for a different size bed or frame, is a different problem:

![Angle bisection][9]
>For good stability in a three-groove kinematic coupling, the normals to the planes containining the contact force vectors should bisect the angles between the balls.  
<cite>&mdash; (Slocum, A. H. (Design of three-groove kinematic couplings [(1992)][8])</cite>

And since I didn't change that, I don't really have the calculations, but it should be easy to figure out given the theory above.



[1]: https://github.com/vzbot3d/VzBoT-UserMods/tree/master/pbsuper/VZTrident/VZT330_400/TripleZ
[2]: https://mandalaroseworks.com/products/internally-threaded-ball?_pos=1&_sid=432d9661c&_ss=r
[3]: https://www.mcmaster.com/aluminum-spacers/aluminum-unthreaded-spacers/
[4]: https://www.amazon.com/gp/product/B0B6NPPB7K
[5]: https://www.amazon.com/gp/product/B07YKZJB6Z
[6]: images/ball_calc.png
[7]: https://pergatory.mit.edu/kinematiccouplings/html/about/kinematic.html
[8]: https://pergatory.mit.edu/kinematiccouplings/documents/Papers/three_ball_and_groove_couplings/Design_of_Three-groove_kinematic_couplings.pdf
[9]: images/groove_drawing.png
[10]: images/mounted_block.png
[11]: images/top_view.png
[12]: images/assembly_01.png