
```table-of-contents

```
# Summary
You will place your CSV file into this folder. Create a text file called `RailCarWeights.txt` within this folder. For testing, add the first three lines from the sample report below. Implement the following class definition.

Properties can be auto-implemented. The SerialNumber is a read-only property returning a concatenated string of CarId and Owner.

# CarWeight Class
![[Pasted image 20231102154027.png]]
## Declaring an Enum
#ENUM
~~~C#
public enum RailCarType
    {
        BOX_CAR,
        COAL_CAR,
        COVERED_HOPPER,
        OIL_TANK
    }
~~~
![[Pasted image 20231102154107.png]]
### `Pages you create should have a feed back and error message area` 


# WeightReport.Razor Component
Add a "Weight Report" component to display the recording of railcar scale weights from a CSV file. A mockup image of the required report is supplied. You will supply an appropriate title for the component. You will read the file and create a collection using your CarWeight class. Your component will display this collection. Display a message if the collection is empty.

[![WeightReport](https://github.com/CPSC-1517/Take-Home-Exercises-Sep-2023/raw/main/Exercise3/ReportWebPage.png)](https://github.com/CPSC-1517/Take-Home-Exercises-Sep-2023/blob/main/Exercise3/ReportWebPage.png)

# WeightScale.razor Component

Add a "Weight Scale" component to allow the recording of railcar scale weights to a CSV file (append mode). A mockup image of the required component is supplied. Your component does not need to have the same layout **but** must use the variety of controls within the mockup for the same data. You will validate the incoming data and display any fields in error. Individual unique error messages will be used to indicate the error. The owner selection and serial number combined make up the railcar serial number.

## Validation
- All fields are required.
- Scale weight must be numeric.

[![WeightScale](https://github.com/CPSC-1517/Take-Home-Exercises-Sep-2023/raw/main/Exercise3/DataWebPage.png)](https://github.com/CPSC-1517/Take-Home-Exercises-Sep-2023/blob/main/Exercise3/DataWebPage.png)

## Submit Buttons

- **Record** will validate the incoming data and save to the CSV file if correct.
- **Clear** will reset the fields to empty input state.
- **Go to Report** will transfer the user to the Weight Report page.

Use the class called `CarWeight` to hold the incoming data. The class diagram has been supplied (above). The ToString() will be used to create the record for the CSV file.
