---
title: Error del compilador C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: dd4374c1a577c4c39c5dec107ed5025d7cdc79c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201701"
---
# <a name="compiler-error-c2865"></a>Error del compilador C2865

' función ': comparación no válida para handle_or_pointer

Puede comparar las referencias a [clases y Structs](../../extensions/classes-and-structs-cpp-component-extensions.md) o tipos de referencia administrados solo para comprobar si hacen referencia al mismo objeto (= =) o a objetos diferentes (! =).

No puede compararlos para su ordenación porque el tiempo de ejecución de .NET podría mover objetos administrados en cualquier momento, cambiando el resultado de la prueba.
