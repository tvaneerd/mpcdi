MPCDI does not allow for non-planar lenses.
We have added fish-eye and anamorphic data as an extension.

We have added an extension called `BufferExtension` which contains extra data for each buffer/region as necessary.

Example:

    <extensionSet>
        <extension Name="BufferExtension" hasExternalFiles="false">
            <buffer id="wolf_90_markerless.cal">
                <region id="Staging Projector_01">
                    <fisheye>
                        <horizontalOffset>.20000</horizontalOffset>
                        <verticalOffset>-.10000</verticalOffset>
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
