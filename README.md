# Eagle IDF4 Exporter

Exports Eagle board files to IDF 4 format for ECAD to MCAD conversion. In simple terms it does the following

## Converts
![alt text](https://github.com/lagnajeet/Eagle-IDF4-Exporter/blob/master/ECAD.gif "Eagle CAD file")

## Into
![alt text](https://github.com/lagnajeet/Eagle-IDF4-Exporter/blob/master/MCAD.png "Solidworks 3D render")

IDF 4 specifications can be found at https://www.simplifiedsolutionsinc.com/images/idf_v40_spec.pdf.

### Features
1. Existing features of IDF3 and the following
2. Exports traces and pads
3. Exports Additional tstop or bstops
4. Exports vias as tented or non tented based on the loaded design rules
5. Exports silkscreen as a separate IDF file where the silkscreen is rendered as traces.
6. As all the layers i.e. the board, traces, pads and silkscreen are separate you can apply any color scheam to your 3D model

Circuitworks from solidworks supports IDF 4 but it's still missing the full implementation of the standard. When translating IDF 4 files to solidworks parts the software fails to generate any traces in the bottom layer. I got around this problem by saving the IDF 4 file to IDX and reopening it in circuitworks. But it also doesn't have very good implementation of idx as well, so the pads get misplaces when saving an IDF 4 file to IDX. So my workaround was the following

1. Filter out pads and components
2. Save file as IDX
3. Close everything and open the IDX file you just saved.
4. convert it into solidworks parts
5. Save the solidworks part file. The part file will be located in the program data folder. Circuitworks saves the actual part file there and opens a document referring to the original file. 
6. Do the same to convert the silkscreen IDF file to IDX
7. Close the idx and open the IDF and this time filterout the traces and convert it into solidworks parts.
8. put the traces, pads and silkscreen together in solidworks main application. Just use some "mates" and they wil fall right into places.
8. You might have to rotate, transtale or mate some of the components on your board afterwards.
