---
title: Escribir un controlador de finalización | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9773817337bce2f054b279724db9859cc2faa41
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462838"
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