---
title: "SetFilters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetFilters"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetFilters (método)"
ms.assetid: ae934e1b-8ead-4c1d-a0f8-e9c80d182340
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# SetFilters
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega filtros de origen, inclusión y recursos para las carpetas del proyecto.  
  
## Sintaxis  
  
```  
  
      function SetFilters(   
   oProj    
);  
```  
  
#### Parámetros  
 `oProj`  
 Proyecto seleccionado.  
  
## Comentarios  
 Se llama a esta función para agregar filtros de origen, inclusión y recursos para las carpetas del proyecto.  Esta función busca los siguientes símbolos en el proyecto:  
  
-   SOURCE\_FILTER  
  
-   INCLUDE\_FILTER  
  
-   RESOURCE\_FILTER  
  
 Estos símbolos contienen las extensiones de archivo utilizadas para filtrar.  
  
## Ejemplo  
  
```  
// Create and set the project name and path.  
selProj = CreateProject(strProjectName, strProjectPath);  
// Add the previously-identified configurations to the project.  
AddConfigurations(selProj, strProjectName);  
// Set filters for the project.  
SetFilters (selproj);  
// Indicate that the project is an ATL project.  
selProj.Object.keyword = "AtlProj";  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)