---
title: "SetCommonPchSettings | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetCommonPchSettings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetCommonPchSettings (método)"
ms.assetid: 12f5524b-f654-4222-b979-8ee0d9f58c14
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# SetCommonPchSettings
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Establece la configuración del encabezado precompilado del proyecto.  
  
## Sintaxis  
  
```  
  
      function SetCommonPchSettings(   
   oProj    
);  
```  
  
#### Parámetros  
 `oProj`  
 Proyecto seleccionado.  
  
## Comentarios  
 Se llama a esta función para establecer la configuración del encabezado precompilado del proyecto.  
  
 Esta función establece la propiedad <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A> en los siguientes valores:  
  
-   **pchUseUsingSpecific** Utiliza la opción del compilador [\/Yu \(usar el archivo de encabezado precompilado\)](../build/reference/yu-use-precompiled-header-file.md).  
  
-   **pchCreateUsingSpecific** Utiliza la opción del compilador [\/Yc \(crear el archivo de encabezado precompilado\)](../build/reference/yc-create-precompiled-header-file.md).  
  
## Ejemplo  
  
```  
if ((strAppType == "LIB" || ((strAppType == "CONSOLE") &&   
   wizard.FindSymbol(SUPPORT_MFC"))) && !Pch)  
   {  
      AddFilesToProject(selProj, strProjectName, InfFile);  
      SetNoCommonPchSettings(selProj);  
   }  
else  
   {  
      AddFilesToProject(selProj, strProjectName, InfFile);  
      SetcommonPchSettings(selProj);  
   }  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [SetNoPchSettings](../ide/setnopchsettings.md)   
 [AddCommonConfig](../ide/addcommonconfig.md)