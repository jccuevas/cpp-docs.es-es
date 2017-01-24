---
title: "CreateInfFile | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CreateInfFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateInfFile (método)"
ms.assetid: 941ea2ce-db10-428e-b423-8dc2a7e825cf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CreateInfFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea el archivo Templates.inf del asistente.  
  
## Sintaxis  
  
```  
  
function CreateInfFile( );  
  
```  
  
## Valor devuelto  
 Archivo de plantilla del asistente.  
  
## Comentarios  
 Se llama a esta función para crear el archivo Templates.inf del asistente a partir del archivo Templatesinf.txt, archivo de texto temporal que se crea primero en el directorio temporal, de acuerdo con las selecciones del usuario.  Templates.inf contiene la lista de los nombres de archivo creados por el asistente.  Vea [El archivo de plantilla](../ide/template-files.md) para obtener más información.  
  
 Si la función no puede crear el archivo Templatesinf.txt en el directorio temporal, mostrará un mensaje de error.  
  
## Ejemplo  
 Vea [AddFilesToProject](../ide/addfilestoproject.md).  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [AddFilesToProject](../ide/addfilestoproject.md)   
 [SetFilters](../ide/setfilters.md)   
 [AddFilesToProject](../ide/addfilestoproject.md)