MPCDI does not allow for non-planar lenses.
We have added fish-eye and anamorphic data as an extension.

We have added an extension called `BufferExtension` which contains extra data for each buffer/region as necessary.
Note that `<fisheye>` also contains horizontal and vertical offset info - this can typically be calculated from the `<frustum>` node, but in the case of a 180 degree fisheye, you would get divide by zero :-/ So we instead just added the numbers you really want, directly.

Example:

    <extensionSet>
        <extension Name="BufferExtension" hasExternalFiles="false">
            <buffer id="wolf_90_markerless.cal">
                <region id="Staging Projector_01">
                    <fisheye>
                        <horizontalOffset>0.20000</horizontalOffset>
                        <verticalOffset>-0.10000</verticalOffset>
                        <f1>0.29907</f1>
                        <f3>-0.0002311605</f3>
                        <f5>0.0000060483</f5>
                        <f7>-0.0000000747</f7>
                    </fisheye>
                    <anamorphic>
                        <angle>0.01000</angle>
                        <aspect>1.20000</aspect>
                    </anamorphic>
                </region>
            </buffer>
        </extension>
        <extension Name="MystiqueExtension" hasExternalFiles="false">
            <GeneratedBy>Mystique Install (Engineering Build) 2.2.0.0 Jan 14 2019</GeneratedBy>
        </extension>
    </extensionSet>


## What are those `f1,f3,f5,f7` numbers?

These are the **fisheye coefficients**. A typical, _equidistant_ fisheye lens follows this equation

> r = f⋅θ

See also https://en.wikipedia.org/wiki/Fisheye_lens

So light entering a lens (ie for a camera) comes in at an angle `θ` (in radians, say). `f` is the focal length. `r` is the distance between the resulting pixel on the camera flim/sensor and the center of the film/sensor.

`f` is typically measured in `mm`.  However, if you only have the resultant image, not the actual lens, you can only measure `r` in terms of pixels. This means `f` is measured in `pixels/radians`.

Note that is the equation of light _entering_ the lens of a camera, and landing on the sensor.  We are more concerned with light _exiting_ the lens of a projector.  The equation is the same, but we are now talking about DMD pixels, not sensor pixels.

### Add in reality

> In theory, there is no difference between theory and reality, but in reality...

Lens are not perfect.  Nor centered.

To account for lens distortions, or a more generic lens model, a more complicated function (similar to Taylor expansion) can be used:

> r = f<sub>1</sub>⋅θ + f<sub>2</sub>⋅θ<sup>2</sup> + f<sub>3</sub>⋅θ<sup>3</sup> + f<sub>4</sub>⋅θ<sup>4</sup> + f<sub>5</sub>⋅θ<sup>5</sup> + f<sub>6</sub>⋅θ<sup>6</sup> + f<sub>7</sub>⋅θ<sup>7</sup>...

Now, it turns out that only the odd coefficients are needed (you want an odd curve, not even, ...vigour hand waving... etc etc...).  And the coefficients get smaller and smaller, so there isn't much sense going past `f7`, so:
    
> r = f<sub>1</sub>⋅θ + f<sub>3</sub>⋅θ<sup>3</sup> + f<sub>5</sub>⋅θ<sup>5</sup> + f<sub>7</sub>⋅θ<sup>7</sup>
    

