---
title: "Running the Analysis Services Deployment Wizard | Microsoft Docs"
description: Learn how to run the SQL Server Analysis Services Deployment Wizard, either interactively or from the command prompt.
ms.date: 02/20/2020
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
monikerRange: "asallproducts-allversions || azure-analysis-services-current || power-bi-premium-current || >= sql-analysis-services-2016"
---
# Running the Analysis Services Deployment Wizard

[!INCLUDE[ssas-appliesto-sqlas-all-aas-pbip](../includes/ssas-appliesto-sqlas-all-aas-pbip.md)]

  The Deployment Wizard can be run the following ways:  
  
-   **Interactively** When run interactively, the Deployment Wizard generates a deployment script based on the input files, as modified interactively by user input. The wizard applies any user modifications only to the deployment script. The wizard does not modify the input files. For more information about the input files, see [Understanding the input files used to create the deployment script](../../analysis-services/deployment/deployment-script-files-input-used-to-create-deployment-script.md).  
  
-   **From the command prompt** When run at the command prompt, the Deployment Wizard generates a deployment script based upon the switches that you use to run the wizard. The wizard may any one of the following: prompt you for user input and modify input files based on that input; run a silent, unattended deployment using the input files as is; or create a deployment script that you can use later.  
  
## Running the Deployment Wizard interactively

 When you run interactively, the Deployment Wizard reads the values from the input files and presents this information to you. You can modify these input values-such as deployment destination, configuration settings, deployment options, and connection string passwords-or leave them as is. If you change any input values, the wizard uses these changes when generating the deployment script. However, the wizard does not make any changes to the values in the input file.  
  
> [!NOTE]  
>  If you want to have the Deployment Wizard modify the input values, run the wizard at the command prompt and set the wizard to run in answer file mode.  
  
 After you review the input values and make any wanted changes, the wizard generates the deployment script. You can run this deployment script immediately on the destination server or save the script for later use.  
  
#### To run the Analysis Services Deployment Wizard interactively
  
-   Click **Start** > **Microsoft SQL Server** > **Deployment Wizard**.  
  
     -or-  
  
-   In the **Projects** folder of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, double-click the \<project name>.asdatabase file.
    > [!NOTE]  
    >  If you cannot find the .asdatabase file, try using Search and specify *.asdatabase. Or, you may need to build the project in SSDT.  
  
## Running the Analysis Services Deployment Wizard at the command prompt

 The Deployment Wizard can also be run at the command prompt. When you run the wizard at the command prompt, you provide the full path to the .asdatabase file and  run the wizard in one of the following modes:  
  
 **Answer file mode**  
 In answer file mode, the wizard lets you interactively modify the input files that were originally generated when the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project was built in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. The wizard saves these modified input files before generating the deployment script. The modified input files become the new starting point the next time that the wizard is run.  
  
 To run the wizard in answer file mode, use the **/a** switch.  
  
 **Silent mode**  
 In silent mode, the wizard runs a silent, unattended deployment based on the information resident in the input files.  
  
 To run the wizard in silent mode, use the **/s** switch. When you run the wizard in silent mode, messages are output to the console or to a log file if one is provided.  
  
 **Output mode**  
 In output mode, the wizard generates a deployment script for later execution based on the input files.  
  
 To run the wizard in output mode, use the **/o** switch and provide an output file name.  
  
 For more information about these command line switches, see [Deploy model solutions with the Deployment Utility](../../analysis-services/deployment/deploy-model-solutions-with-the-deployment-utility.md).  
  
#### To run the Analysis Services Deployment Wizard at the command prompt
  
1.  If installed with SSMS 18.x, open a command prompt and navigate to the default path C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE. If installed with SSMS 17.x, the default path is C:\Program Files (x86)\Microsoft SQL Server\140\Tools\Binn\ManagementStudio.
  
2.  Type **Microsoft.AnalysisServices.Deployment.exe** followed by the switches that correspond to the mode in which you want to run the wizard.  
  
## See Also  
 [Understanding the Analysis Services deployment script](../../analysis-services/deployment/understanding-the-analysis-services-deployment-script.md)   
 [Deploy model solutions by using the Deployment Wizard](../../analysis-services/deployment/deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
