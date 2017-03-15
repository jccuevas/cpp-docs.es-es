---
title: "GetProjectFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetProjectFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProjectFile (método)"
ms.assetid: e5fdc468-755a-4b4e-81bd-e63881531bed
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# GetProjectFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Devuelve el tipo especificado de nombre de archivo.  
  
## Sintaxis  
  
```  
  
      function GetProjectFile(   
   oProj,   
   strType,   
   bFullPath,   
   bMFC    
);  
```  
  
#### Parámetros  
 oProj  
 Proyecto seleccionado.  
  
 `strType`  
 Tipo de archivo que va a recuperarse \(por ejemplo, STDAFX, RC, IDL, CPP, H, ODL o DEF\).  
  
 *bFullPath*  
 Marcador que especifica si ha de devolver el nombre completo de la ruta de acceso.  
  
 *bMFC*  
 Indica si el proyecto es un proyecto basado en MFC.  Si `strType` es .cpp o .h, se considerará basado en MFC.  De lo contrario, se asumirá que el proyecto está basado en ATL.  
  
## Valor devuelto  
 El nombre de archivo del tipo por proyecto de los archivos.  
  
## Comentarios  
 Se llama a esta función para obtener el nombre de archivo del tipo especificado en el proyecto especificado.  
  
## Ejemplo  
  
```  
// The selected MFC project's CPP file is retrieved and   
// assigned to strFileName.  
var strFileName = GetProjectFile(selProj, "CPP", false, true);  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [GetProjectPath](../ide/getprojectpath.md)   
 [GetUniqueFileName](../ide/getuniquefilename.md)