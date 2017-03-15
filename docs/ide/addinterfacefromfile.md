---
title: "AddInterfaceFromFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AddInterfaceFromFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddInterfaceFromFile (método)"
ms.assetid: fa848690-ad98-4fb4-bbcf-dffcaad05df2
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# AddInterfaceFromFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa e inserta un archivo de plantilla que contiene una interfaz.  
  
## Sintaxis  
  
```  
  
      function AddInterfaceFromFile(   
   oCM,   
   strInterfaceFile    
);  
```  
  
#### Parámetros  
 `oCM`  
 Objeto [Visual C\+\+ Code Model](http://msdn.microsoft.com/es-es/dd6452c2-1054-44a1-b0eb-639a94a1216b).  
  
 *strInterfaceFile*  
 Nombre del archivo de plantilla \(únicamente el nombre, sin ruta de acceso\).  
  
## Comentarios  
 Se llama a esta función para representar e insertar en el archivo .idl del proyecto un archivo de plantilla que contiene una interfaz.  
  
 Si la interfaz no se agrega correctamente, esta función mostrará un mensaje de error.  
  
## Ejemplo  
  
```  
// Render myint.idl and insert into strProject.idl  
AddInterfaceFromFile(oCM, "myint.idl");  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)