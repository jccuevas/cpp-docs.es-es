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
ms.openlocfilehash: 29a462f83bff3bab158e9bcf9fa7947efb56a79b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074479"
---
# <a name="restrictions-on-exception-handlers"></a>Restricciones de los controladores de excepciones

La limitación principal de utilizar controladores de excepciones en código es que no se puede usar un **goto** instrucción para saltar en un **__try** bloque de instrucciones. En su lugar, se debe especificar el bloque de instrucciones a través del flujo de control normal. Puede saltar fuera de un **__try** instrucción en bloques y anidar los controladores de excepciones como desee.

## <a name="see-also"></a>Vea también

[Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)