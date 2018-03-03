---
title: Escribir un controlador de excepciones | Documentos de Microsoft
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
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52d102f29a015ea077e9ec94a9f1ed63f44f7c1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="writing-an-exception-handler"></a>Escribir un controlador de excepciones
Los controladores de excepciones se utilizan normalmente para responder a errores específicos. Puede utilizar la sintaxis del control de excepciones para filtrar todas las excepciones distintas de las que sabe cómo administrar. Las demás excepciones se deben pasar a otros controladores (posiblemente en la biblioteca en tiempo de ejecución o el sistema operativo) creados para buscar esas excepciones concretas.  
  
 Los controladores de excepciones utilizan la instrucción try-except.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [La instrucción try-except instrucción](../cpp/try-except-statement.md)  
  
-   [Escribir un filtro de excepción](../cpp/writing-an-exception-filter.md)  
  
-   [Generar excepciones de software](../cpp/raising-software-exceptions.md)  
  
-   [Excepciones de hardware](../cpp/hardware-exceptions.md)  
  
-   [Restricciones en los controladores de excepción](../cpp/restrictions-on-exception-handlers.md)  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)