---
title: "NAME (C/C++) | Microsoft Docs"
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
  - "name"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NAME (instrucción de archivo .def)"
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NAME (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica un nombre para el archivo de salida principal.  
  
```  
NAME [application][BASE=address]  
```  
  
## Comentarios  
 Un modo equivalente de especificar un nombre de archivo de salida es con la opción [\/OUT](../../build/reference/out-output-file-name.md) del vinculador, y otro modo equivalente de establecer la dirección base es con la opción [\/BASE](../../build/reference/base-base-address.md) del vinculador.  Si se especifican ambos, \/OUT tiene prioridad sobre **NAME**.  
  
 Si se está compilando una DLL, NAME solo afectará al nombre de la DLL.  
  
## Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)