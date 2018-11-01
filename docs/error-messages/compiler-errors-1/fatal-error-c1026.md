---
title: Error irrecuperable C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: b1a659967a9a62cb79e1084f7d1fa1729bae14da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666207"
---
# <a name="fatal-error-c1026"></a>Error irrecuperable C1026

desbordamiento de la pila del analizador, programa demasiado complejo

El espacio necesario para analizar el programa provocó un desbordamiento de pila del compilador.

Reduzca la complejidad de las expresiones:

- Reduciendo el anidamiento en `for` y `switch` instrucciones. Colocar instrucciones más profundamente anidadas en funciones independientes.

- Dividir expresiones largas que implican los operadores de coma o llamadas de función.