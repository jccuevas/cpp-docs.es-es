---
title: Restricciones en los controladores de excepciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8775f752a541d2a250e9c1c5a0c325b684335988
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464605"
---
# <a name="restrictions-on-exception-handlers"></a>Restricciones de los controladores de excepciones
La limitación principal de utilizar controladores de excepciones en código es que no se puede usar un **goto** instrucción para saltar en un **__try** bloque de instrucciones. En su lugar, se debe especificar el bloque de instrucciones a través del flujo de control normal. Puede saltar fuera de un **__try** instrucción en bloques y anidar los controladores de excepciones como desee.  
  
## <a name="see-also"></a>Vea también  
 [Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)   
 [Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)