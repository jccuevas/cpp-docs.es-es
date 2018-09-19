---
title: Error del compilador C2865 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc0a49f8e6ab42f7e607cd5f4f7cc91f6895abe0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035173"
---
# <a name="compiler-error-c2865"></a>Error del compilador C2865

'function': comparación no válida para handle_or_pointer

Puede comparar las referencias a [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md) o tipos de referencia para la igualdad para comprobar si hacen referencia al mismo objeto (==) o a objetos diferentes administrados (! =).

No se puede compararlos para ordenar porque el tiempo de ejecución .NET podría mover objetos administrados en cualquier momento, cambiar el resultado de la prueba.