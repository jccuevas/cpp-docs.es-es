---
title: Error del compilador C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: 38b7dd86a57c3cd89811c6489e51fb4271fd7b79
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777151"
---
# <a name="compiler-error-c2865"></a>Error del compilador C2865

'function': comparación no válida para handle_or_pointer

Puede comparar las referencias a [clases y Structs](../../extensions/classes-and-structs-cpp-component-extensions.md) o tipos de referencia para la igualdad para comprobar si hacen referencia al mismo objeto (==) o a objetos diferentes administrados (! =).

No se puede compararlos para ordenar porque el tiempo de ejecución .NET podría mover objetos administrados en cualquier momento, cambiar el resultado de la prueba.