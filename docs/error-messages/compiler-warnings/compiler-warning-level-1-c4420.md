---
title: Advertencia del compilador (nivel 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: 72ab87b34e07717112f5af1727a216b4f786ae0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186795"
---
# <a name="compiler-warning-level-1-c4420"></a>Advertencia del compilador (nivel 1) C4420

' Operator ': el operador no está disponible; se usará ' Operator ' en su lugar; la comprobación en tiempo de ejecución puede verse comprometida

Esta advertencia se genera cuando se usa [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector new/delete check) y cuando no se encuentra ninguna forma vectorial. En este caso, se usa la forma no vectorial.

Para que/RTCv funcione correctamente, el compilador debe llamar siempre a la forma de vector de [new](../../cpp/new-operator-cpp.md)/[Delete](../../cpp/delete-operator-cpp.md) si se ha utilizado la sintaxis de vector.
