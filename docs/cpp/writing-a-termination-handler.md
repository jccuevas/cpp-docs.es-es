---
title: "Escribir un controlador de terminación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b9d4099a7f40acf0b5bfcc89f1c95cb880683b86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="writing-a-termination-handler"></a>Escribir un controlador de finalización
A diferencia de los controladores de excepciones, los controladores de terminación se ejecutan siempre, independientemente de si el bloque de código protegido ha finalizado normalmente. El único propósito del controlador de terminación debe ser garantizar que los recursos, como la memoria, los identificadores y los archivos, se cierran correctamente independientemente de cómo termine de ejecutarse una sección de código.  
  
 Los controladores de terminación utilizan la instrucción try-finally.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [La instrucción try-finally](../cpp/try-finally-statement.md)  
  
-   [Limpiar recursos](../cpp/cleaning-up-resources.md)  
  
-   [Cronología de las acciones de control de excepciones](../cpp/timing-of-exception-handling-a-summary.md)  
  
-   [Restricciones en los controladores de terminación](../cpp/restrictions-on-termination-handlers.md)  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)