---
title: "Escribir un controlador de excepciones | Microsoft Docs"
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
  - "control de excepciones, controladores de excepciones"
  - "control estructurado de excepciones, controladores de excepciones"
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Escribir un controlador de excepciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controladores de excepciones se utilizan normalmente para responder a errores específicos.  Puede utilizar la sintaxis del control de excepciones para filtrar todas las excepciones distintas de las que sabe cómo administrar.  Las demás excepciones se deben pasar a otros controladores \(posiblemente en la biblioteca en tiempo de ejecución o el sistema operativo\) creados para buscar esas excepciones concretas.  
  
 Los controladores de excepciones utilizan la instrucción try\-except.  
  
## ¿Qué más desea saber?  
  
-   [La instrucción try\-except](../cpp/try-except-statement.md)  
  
-   [Escribir un filtro de excepciones](../cpp/writing-an-exception-filter.md)  
  
-   [Producir excepciones de software](../cpp/raising-software-exceptions.md)  
  
-   [Excepciones de hardware](../cpp/hardware-exceptions.md)  
  
-   [Restricciones en los controladores de excepciones](../cpp/restrictions-on-exception-handlers.md)  
  
## Vea también  
 [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)