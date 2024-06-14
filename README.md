This repository contains a few examples on how TTool and ChatGPT perform.

# Directory organization

There are three subdirectories. Each one contains a desc file, with the system specification, and a TTool file featuring five outputs produced by TTool + ChatGPT 3.5, with NO human modification, apart from a better placement of graphical components.

The main directory also contains this README and the results in results.ods: these results give the time to obtain the diagrams, and their quality. This quality is compared with one of the diagrams made by master-level students after 21h of lectures ands labs.

# Model generation

## How to look at the models we have obtained?

- You first need to install TTool
- Then, with TTool, open one of the .xml files located in the subdirectory. For instance, to look at the platooning model, open platooning/platoonings.xml 

## How to reproduce the results?

- You first need to install TTool
- You then need to get a valid OPENAI key
- You need to change the config.xml file of your TTool installation (see https://ttool.telecom-paris.fr/ttoolai.html):

Add this (and correctly set your key):
<OPENAIKey data="your key/>
<OPENAIModel data="gpt-3.5-turbo gpt-4-0125-preview"/> 

- You can start TTool, and use the AI dialog windows. There, you put the system specification in the question area, and you have to select, to identify blocks: "Identify system blocks (knowledge type #2 with slicing) - Provide a system specification". Then, click on start.

Once the blocks have been determined, click on "apply response", and close the AI window.

- To identify state machines: select a block diagram, open the AI window, put in the question field the system specification, and select "Identify state machines and attributes - Select a block diagram. Additionally, you can provide a system specification". Click on start. Once state machine have been computed, select "apply response". You should now have both block and state machine diagrams.

Since ChatGPT is based on randomness to produce the results, it is very likely you will get results different from ours. Try several times to figure out the differences you may obtain.


# Incoherency detection and correction

- Go to "incoherencies" directory
- There, there are 3 .xml files to be opened with TTool. Do configure TTool as explained before in the "model generation" section.

 ## Model content
 Each file contains 2 block diagrams (BD) and 2 Use case diagrams (UCD) automatically generated using the system specification. They also contain the  models corrected thansk to the detection of incoherencies. These incoherencies are given in the updated models.

## How to reproduce the results?

Let us assume that you have opened with TTool a model, for instance spacebasedystem.xml. We assume that TTool is correcly configured to use ChatGPT.

### Detecting incoherencies between diagrams

Select a block diagram (BD1 or BD2), make a right click, "to textual format". Do the same for UCD1 or UCD2.

Now, open the AI window (use the icon on the right depicting a brain), then select "Identify incoherencies". In the question box, put:
- specification: the specification of the system
- Diagram1: Use case diagram. There, paste the textual format of the UCD you have selected before
- Diagram2: Block diagram. There, paste the textual format of the BD you have selected just before

The question box should now contain the system specification, then the textual description of the UCD, then the textual description of the BD. Now, click on "start". If TTool was able to exchange with ChatGPT, then you should obtain a list of incoherencies, that could look like this:

```
AI: json
{
  "incoherencies": [
    {
      "diagram": "Diagram1",
      "description": "There is no actor or use case for ErrorCorrectionCode, which is a significant part of the system as per the specification."
    },
    {
      "diagram": "Diagram1",
      "description": "Use case 'Monitor_Safety_Data' is shown to be associated with RF_Receiver, which is incorrect as monitoring is a ground station activity."
    },
    {
      "diagram": "Diagram2",
      "description": "Block 'GroundStation' has attributes for temperature, batteryLevel, and fuelQuantity, which are not its attributes but those of the space-based system."
    },
    {
      "diagram": "Diagram2",
      "description": "Signal 'tM_7978(int value)' in RFTransmitter and its corresponding relation are unaccounted for in Diagram1."
    },
    {
      "diagram": "Diagram2",
      "description": "Signal 'memoryWriteCRC()' and 'memoryReadCRC()' in 'ErrorCorrectionCode' block have no corresponding use cases or activities in Diagram1."
    },
    {
      "diagram": "Diagram2",
      "description": "There is no block representing the Watchdog's activity of checking if tasks are still responsive, which is a critical system function as per the specification."
    },
    {
      "diagram": "Diagram2",
      "description": "There is no representation for the cancellation and recomputation of TM upon receiving another TC, as described in the specification."
    },
    {
      "diagram": "Diagram2",
      "description": "The association of 'Microcontroller' with the task of restarting the system if tasks are unresponsive is not clearly translated into relationships with other blocks."
    }
  ]
}
```

### Updating diagrams from incoherencies

Imagine that you now wish to update the block diagram considering these inconsistencies. Open the AI window of TTool. Select at the top "system blocks". In the question field, put:
- "Specification:" followed with the system specification
- "Diagram1, use case diagram:" followed with the textual description of your selected UCD
- "Diagram2, block diagram:" followed with the textual description of your selected BD
- the following text, taken from incoherencies:
```
Do correct the block diagram considering the following incoherencies:
1. Block 'GroundStation' has attributes for temperature, batteryLevel, and fuelQuantity, which are not its attributes but those of the space-based system
2. Signal 'tM_7978(int value)' in RFTransmitter and its corresponding relation are unaccounted for in Diagram1
3. There is no block representing the Watchdog's activity of checking if tasks are still responsive, which is a critical system function as per the specification
4. There is no representation for the cancellation and recomputation of TM upon receiving another TC, as described in the specification
5. The association of 'Microcontroller' with the task of restarting the system if tasks are unresponsive is not clearly translated into relationships with other blocks
Do correct incoherency 1-5 to propose a new block diagram.

```
Click on start, wait. Then click on apply, and reorganize the blocks: you should have an updated Block Diagram.






Enjoy!
