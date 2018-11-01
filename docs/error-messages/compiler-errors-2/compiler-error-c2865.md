---
title: Error del compilador C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: e95714f7a10c1c25562e8b12025ede486e66cff8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532759"
---
# <a name="compiler-error-c2865"></a>Error del compilador C2865

'function': comparación no válida para handle_or_pointer

Puede comparar las referencias a [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md) o tipos de referencia para la igualdad para comprobar si hacen referencia al mismo objeto (==) o a objetos diferentes administrados (! =).

No se puede compararlos para ordenar porque el tiempo de ejecución .NET podría mover objetos administrados en cualquier momento, cambiar el resultado de la prueba.