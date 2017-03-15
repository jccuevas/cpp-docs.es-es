---
title: "AddCoclassFromFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AddCoclassFromFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddCoclassFromFile (método)"
ms.assetid: a8a211fd-2df3-4361-8137-9c0d999b7f88
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# AddCoclassFromFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa e inserta en el archivo .idl del proyecto un archivo de plantilla que contiene una coclase.  
  
## Sintaxis  
  
```  
  
      function AddCoclassFromFile(   
   oCM,   
   strCoclassFile    
);  
```  
  
#### Parámetros  
 `oCM`  
 Objeto [Visual C\+\+ Code Model](http://msdn.microsoft.com/es-es/dd6452c2-1054-44a1-b0eb-639a94a1216b).  
  
 *strCoclassFile*  
 Nombre del archivo de plantilla, excluida la ruta de acceso.  
  
## Comentarios  
 Se llama a esta función para representar e insertar en el archivo .idl del proyecto un archivo de plantilla que contiene una coclase.  
  
## Ejemplo  
  
```  
// Render myproj.idl and insert into the project's .idl.  
AddCoclassFromFile(oCM, "myproj.idl");  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)