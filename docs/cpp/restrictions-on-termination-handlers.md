---
title: "Restricciones de los controladores de finalizaci&#243;n | Microsoft Docs"
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
  - "restricciones, controladores de terminación"
  - "controladores de terminación, limitaciones"
  - "try-catch (palabra clave) [C++], controladores de terminación"
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Restricciones de los controladores de finalizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

No puede utilizar una instrucción `goto` para saltar dentro de un bloque de instrucciones `__try` o un bloque de instrucciones `__finally`.  En su lugar, se debe especificar el bloque de instrucciones a través del flujo de control normal. \(Sin embargo, puede saltar fuera de un bloque de instrucciones `__try`\). Además, no puede anidar un controlador de excepciones ni un controlador de finalización dentro de un bloque de instrucciones `__finally`.  
  
 Además, algunos tipos de código permitidos en un controlador de finalización generan resultados cuestionables, por lo que deben utilizarse con precaución, si se utilizan.  Uno de ellos es una instrucción `goto` que salta fuera de un bloque de instrucciones `__finally`.  Si el bloque se ejecuta como parte de una finalización normal, no sucede nada inusual.  Pero si el sistema está desenredando la pila, el desenredado se detiene y la función actual obtiene el control como si no hubiera una finalización anómala.  
  
 Una instrucción `return` dentro de un bloque de instrucciones `__finally` presenta casi la misma situación.  El control se devuelve al llamador inmediato de la función que contiene el controlador de finalización.  Si el sistema estaba desenredando la pila, este proceso se detiene y el programa continúa como si no se hubiera producido una excepción.  
  
## Vea también  
 [Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)   
 [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)