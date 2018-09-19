---
title: Error irrecuperable C1026 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db9167383df48dad274ef8941defaa53f51d3bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068993"
---
# <a name="fatal-error-c1026"></a>Error irrecuperable C1026

desbordamiento de la pila del analizador, programa demasiado complejo

El espacio necesario para analizar el programa provocó un desbordamiento de pila del compilador.

Reduzca la complejidad de las expresiones:

- Reduciendo el anidamiento en `for` y `switch` instrucciones. Colocar instrucciones más profundamente anidadas en funciones independientes.

- Dividir expresiones largas que implican los operadores de coma o llamadas de función.