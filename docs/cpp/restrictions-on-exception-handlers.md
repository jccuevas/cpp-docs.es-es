---
title: "Restricciones de los controladores de excepciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones, controladores de excepciones"
  - "restricciones, controladores de excepciones"
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Restricciones de los controladores de excepciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La limitación principal de usar los controladores de excepciones en el código es que no se puede utilizar una instrucción `goto` para saltar a un bloque de instrucciones `__try`.  En su lugar, se debe especificar el bloque de instrucciones a través del flujo de control normal.  Puede saltar fuera de un bloque de instrucciones `__try` y anidar los controladores de excepciones a su elección.  
  
## Vea también  
 [Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)   
 [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)