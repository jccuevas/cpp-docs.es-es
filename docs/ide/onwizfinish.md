---
title: "OnWizFinish | Microsoft Docs"
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
  - "OnWizFinish"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnWizFinish (método)"
ms.assetid: 5e0790c3-c5b4-43de-b9db-b18d07c19f41
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OnWizFinish
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se llama a esta función desde el script HTML del asistente cuando el usuario hace clic en **Finalizar**.  A su vez, esta función llama a la función **Finish** del control del asistente.  
  
## Sintaxis  
  
```  
  
      function OnWizFinish(   
   document    
);  
```  
  
#### Parámetros  
 `document`  
 Objeto de documento HTML.  
  
## Comentarios  
 El script HTML del asistente llama a esta función cuando el usuario hace clic en **Finalizar**.  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)