---
title: "Escribir un controlador de finalizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones, controladores de terminación"
  - "excepciones, terminar"
  - "controladores"
  - "controladores, terminación"
  - "control estructurado de excepciones, controladores de terminación"
  - "controladores de terminación"
  - "controladores de terminación, escribir"
  - "try-catch (palabra clave) [C++], controladores de terminación"
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Escribir un controlador de finalizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A diferencia de los controladores de excepciones, los controladores de terminación se ejecutan siempre, independientemente de si el bloque de código protegido ha finalizado normalmente.  El único propósito del controlador de terminación debe ser garantizar que los recursos, como la memoria, los identificadores y los archivos, se cierran correctamente independientemente de cómo termine de ejecutarse una sección de código.  
  
 Los controladores de terminación utilizan la instrucción try\-finally.  
  
## ¿Qué más desea saber?  
  
-   [Instrucción try\-finally](../cpp/try-finally-statement.md)  
  
-   [Limpiar los recursos](../cpp/cleaning-up-resources.md)  
  
-   [Cronología de las acciones en el control de excepciones](../cpp/timing-of-exception-handling-a-summary.md)  
  
-   [Restricciones en los controladores de terminación](../cpp/restrictions-on-termination-handlers.md)  
  
## Vea también  
 [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)