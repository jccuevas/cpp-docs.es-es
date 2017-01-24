---
title: "GetExportPragmas | Microsoft Docs"
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
  - "GetExportPragmas"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetExportPragmas (método)"
ms.assetid: ef21f6a3-d83f-4e19-9323-ca28cc40c8fd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetExportPragmas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega directivas pragma para exportar funciones.  
  
## Sintaxis  
  
```  
  
function GetExportPragmas( );  
  
```  
  
## Valor devuelto  
 Una cadena con las directivas pragma de exportación.  Puede ser una de las siguientes:  
  
-   `#pragma comment(linker, "/EXPORT:DllCanUnloadNow=_DllCanUnloadNow@0,PRIVATE")'`  
  
-   `#pragma comment(linker, "/EXPORT:DllGetClassObject=_DllGetClassObject@12,PRIVATE")`  
  
-   `#pragma comment(linker, "/EXPORT:DllRegisterServer=_DllRegisterServer@0,PRIVATE")`  
  
-   `#pragma comment(linker, "/EXPORT:DllUnregisterServer=_DllUnregisterServer@0,PRIVATE")`  
  
## Comentarios  
 Se llama a esta función para agregar directivas pragma con el fin de exportar funciones.  
  
## Ejemplo  
  
```  
oDllCanUnloadNow.StartPoint.Insert(GetExportPragmas() + "\r\n");  
oCM.Synchronize();  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [comentario](../preprocessor/comment-c-cpp.md)