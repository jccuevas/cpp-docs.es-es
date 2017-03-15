---
title: "SetMergeProxySymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetMergeProxySymbol"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetMergeProxySymbol (método)"
ms.assetid: d6a9db59-2d5b-4431-98bc-785675e0eafe
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# SetMergeProxySymbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El asistente llama a esta función para agregar el símbolo \_MERGE\_PROXYSTUB en caso de que sea necesario.  
  
## Sintaxis  
  
```  
  
      function SetMergeProxySymbol(   
   oProj    
);  
```  
  
#### Parámetros  
 `oProj`  
 Objeto de proyecto seleccionado.  
  
## Comentarios  
 El asistente llama a esta función para agregar el símbolo \_MERGE\_PROXYSTUB en caso de que sea necesario.  
  
## Ejemplo  
  
```  
SetMergeProxySymbol (selproj);  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)