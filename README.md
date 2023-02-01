# Blue Prism Business Object Library (BOL) Generation Tool
## Installation and User Guide

Document Revision 1.0.6

# Trademarks and copyright
The information contained in this document is the proprietary and confidential information of Blue Prism Limited and should not be disclosed to a third party without the written consent of an authorized Blue Prism representative. No part of this document may be reproduced or transmitted in any form or by any means, electronic or mechanical, including photocopying without the written permission of Blue Prism Limited. All trademarks are hereby acknowledged and are used to the benefit of their respective owners. Blue Prism and its affiliates are not responsible for the content of external websites referenced by this document.

## Introduction
The following document outlines the installation and configuration instructions to use this tool. The Blue Prism Business Object Library (BOL) Generation tool is the culmination of hands-on experience helping customers streamline their Design Authority processes and provide a quick, easy and simple way to share a snapshot of a business processes and objects in any Blue Prism development database.

## Installation & Configuration

## Installing the .Net Libraries
Extract the bol\_vX.X.X.zip archive to location of your choice. (i.e., C:\BluePrism)

Move the following .Net Library files from your chosen location into the Blue Prism working directory

| **Library** | **Description** |
| --- | --- |
| **DesignAuthorityTools.BOL.dll** | This is the .Net library that contains the logic for the BOL generator. |
| **Handlebars.dll** | Handlebars.net version 2.1.2.0 this is the .Net library for the template engine used to build the indexes and pages in the DesignAuthorityTools.BOL.dll library. |
(i.e., C:\Program Files\Blue Prism Limited\Blue Prism Automate)

![image](https://user-images.githubusercontent.com/58272708/199320331-f7960673-f7af-4f7a-aaea-7e62ca789cd2.png)

![](RackMultipart20221101-1-nqvlgd_html_ee1d1ca3268d363e.png)

## Configuring the Folder Structure

The BOL Generation process comes preconfigured to use the following folder structure:
![image](https://user-images.githubusercontent.com/58272708/199320387-d04d0fdf-94ee-49bd-a60e-b3fcbed4693f.png)
| **Folder** | **Description** |
| --- | --- |
| **C:\BluePrism** | The root directory |
| **C:\BluePrism\BOL\input** | The directory that process xml files will be exported to out of the targeted database and stored for use as input to the BOL generation tool. |
| **C:\BluePrism\BOL\output** | The output directory which the BOL generation tool will output the generated html BOL documents. |

_ **Important Note:** _

_The root directory and input/output folders can be anything you like but they must exist prior to running the process and must be configured in the Main Page data items of the BOL Generation process._

Installing the BP Release file

Import the **bolgen\_vX.X.X.bprelease** file that came with the .Net libraries into the target Blue Prism environment and configure the data items of the process to match your credentials and folder structure. Ensure the correct Connection is configured then publish and run the process in control room.

![image](https://user-images.githubusercontent.com/58272708/199320757-98eaa8b3-f98c-4b1a-9e8a-5df6ed7488f5.png)

![image](https://user-images.githubusercontent.com/58272708/199320785-620409cb-08d2-444d-9873-dd7a02675e72.png)

After the import is complete restart Blue Prism and login to ensure the newly added .Net libraries are added to Blue Prism

## Configuring the BP Release File

The following variables can be configured in the BOL Generation process itself on the Main Page via the data items.

![image](https://user-images.githubusercontent.com/58272708/199320815-8c877fa6-8ed2-4c0f-8075-3ec3a8cb5221.png)

| **#** | **Data Item** | **Description** | **Default** |
| --- | --- | --- | --- |
| **1** | Blue Prism Directory | The location of the AutomateC.exe file. | C:\Program Files\Blue Prism Limited\Blue Prism Automate |
| **2** | Blue Prism DB Connection | This will be the name of your Connection to the Blue Prism database used at Login to BP Studio. | Support |
| **3** | Export Directory | The directory that process xml files will be exported to out of the targeted database and stored for use as input to the BOL generation tool. | C:\BluePrism\BOL\input |
| **4** | Output Directory | The output directory which the BOL generation tool will output the generated html BOL documents. | C:\BluePrism\BOL\output |
| **5** | Program Name | The name you want displayed on the BOL generated documents. |
| **6** | Blue Prism Credentials | This is the Blue Prism credentials that will be used by the AutomatC.exe threads to access the database connection and list and export the processes to the Export Directory. | Blue Prism BOL |

Running the tool

You should be able to run this tool just like any other process and with any Blue Prism credentials that can read process and object files.

First Time Run Tips:

It may be best to try each stage in the BOL Generation process one at a time in Debug mode to ensure your credentials are working and your configuration is correct.

It also may be worth taking about 5 or 10 xml files exported and place those into the input directory then run the create BOL stage to make sure everything is working according to plan.

For a database with 378 processes (this includes object processes) the export from the database takes about 5 to 7 minutes using 8 parallels, and the creation of the BOL for 378 processes takes about 2 minutes using 4 parallels.

Once you're comfortable with the process and how it runs you can schedule it to run daily or weekly and put the output on the shared drive.

![image](https://user-images.githubusercontent.com/58272708/199320860-fcad0bf3-6d99-4b7b-80b5-f0d1bfc99dd3.png)

## Expected Output:
The BOL generator will create the folder structure and files in the output directory of the root BOL directory like shown below:

![image](https://user-images.githubusercontent.com/58272708/199320882-56a36e48-f585-4492-944b-30fd7ff355e3.png)

The breakdown of each directory and the information within is as follows:

| **Library** | **Description** |
| --- | --- |
| **C:\BluePrism\BOL\output\index.html** | This is a the landing page that can be customized to have information particular to the customer or C.o.E. |
| ![image](https://user-images.githubusercontent.com/58272708/199320917-fa5339da-69a3-479e-b3f7-9026bff09e15.png) |
| **C:\BluePrism\BOL\output\searchindex.html** | This is the searchable interactive snapshot of all objects ( xml files in the input directory) with the ability to drill down to actions and flow diagrams. |
|![image](https://user-images.githubusercontent.com/58272708/199320938-38009978-b224-45b5-bcea-42c72199d4aa.png) |
| **C:\BluePrism\BOL\output\processes\*.html** | The directory where all of the processes and objects are generated and stored. |
| ![image](https://user-images.githubusercontent.com/58272708/199320981-469fa039-7cf5-42b9-aa6f-184fd0806e58.png) |
| **C:\BluePrism\BOL\output\processes\diagrams\*.html** | The directory where all of the objects action diagrams are generated and stored. |
| ![image](https://user-images.githubusercontent.com/58272708/199321002-0c463cae-1847-4477-9297-be90164e60b0.png) |
| **C:\BluePrism\BOL\output\scripts\*.js** | The location of scripts used by the BOL html pages for look and feel of the process pages and diagrams. |
| **C:\BluePrism\BOL\output\stylesheets\*.css** | The location of scripts used by the bol html pages for look and feel of the process pages and diagrams. |

## Troubleshooting, Tips & Tricks
This is a long running process and may show a warning in the control room. This as expected as there is no communication between the DLL and runtime to tell Blue Prism its progress.

![image](https://user-images.githubusercontent.com/58272708/199321026-bb2c6b0b-39d7-4b97-ab82-065705970a10.png)

You can see that the process is working by looking at the input directory (Export Stage) for xml files being exported…

![image](https://user-images.githubusercontent.com/58272708/199321043-35c7377c-cb37-42f9-908c-d86b5f287a87.png)

and the output directory (Create BOL Stage). For the html document generated files…

![image](https://user-images.githubusercontent.com/58272708/199321064-01d3281d-1441-4272-bea9-a34a9f57ce39.png)

You can also see if the parallel AutomatC.exe threads are running during the Export and Generation stages.

![image](https://user-images.githubusercontent.com/58272708/199321126-c9f71fd9-e8db-4e0e-a280-0104e6b28561.png)

## Advanced Tips:
If you get out of memory exceptions in Blue Prism or want to see if it processes xml files faster configure the Parallels argument to the Export and Create BOL stages this will change the number of parallel processes that will run.

![image](https://user-images.githubusercontent.com/58272708/199321161-e8316e6c-437c-4f4e-bc95-b92b6d531157.png)
![image](https://user-images.githubusercontent.com/58272708/199321196-d0dbc07b-a4e5-42f2-aa8d-b8101324d068.png)

The more parallels the more threads and the faster it can be done. However, there is a limit based on the machine you are running the process on so take caution and experiment.

## Missing Objects and Processes
Some objects and process xml code will be exported by AutomateC.exe but may not generate an html output by the tool or may cause the tool to crash. If you notice there is a gap or discrepancy in the generation tool please let your Blue Prism team know and provide the source code so we can update the tool to accommodate those processes.

## BOL Generation Tool Dependencies:

## .Net Framework
[Download .NET Framework 4.X or Higher | Free official downloads (microsoft.com)](https://dotnet.microsoft.com/en-us/download/dotnet-framework)

## Custom .NET Libraries:
- BOL.dll
  - Custom built .Net library that contains the functions for the BOL generator.
  - Targeted and compiled against .Net Framework v4.8 for v4.0 Runtime or higher

## Open-Source .NET Libraries:
  - [https://www.nuget.org/packages/Handlebars.Net#dependencies-body-tab](https://www.nuget.org/packages/Handlebars.Net#dependencies-body-tab)
  - [https://github.com/Handlebars-Net/Handlebars.Net](https://github.com/Handlebars-Net/Handlebars.Net)

## Open Source JavaScript Libraries:

- DataTables 1.12.1 datatables.net/license
- jQuery JavaScript Library v3.6.0 https://jquery.com/ 
- jQuery UI - v1.13.2 - 2022-07-17 http://jqueryui.com
- Materialize v1.0.0 (http://materializecss.com)
- pace.js v1.2.4 https://github.com/CodeByZach/pace/
- Panzoom.js https://github.com/timmywil/panzoom/blob/main/MIT-License.txt
- jsPlumb.js https://docs.jsplumbtoolkit.com/community

