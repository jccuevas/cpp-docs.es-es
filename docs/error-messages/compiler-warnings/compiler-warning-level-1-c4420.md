---
title: Advertencia del compilador (nivel 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: a4a7e91e7845cc0fc25d5a6fad16ae7b7e327952
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662896"
---
# <a name="compiler-warning-level-1-c4420"></a>Advertencia del compilador (nivel 1) C4420

'operador': operador no disponible, utilizando 'operator' en su lugar; comprobación de tiempo de ejecución puede suponer un riesgo

Esta advertencia se genera cuando se usa el [opción /RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector comprobación new/delete) y cuando no se encuentra ningún formulario de vector. En este caso, se usa el formulario no vectorial.

Orden de la opción /RTCv funcione correctamente, el compilador siempre debe llamar a la forma vectorial de [nueva](../../cpp/new-operator-cpp.md)/[eliminar](../../cpp/delete-operator-cpp.md) si se utiliza la sintaxis de vector.