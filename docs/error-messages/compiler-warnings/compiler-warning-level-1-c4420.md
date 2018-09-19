---
title: Compilador advertencia (nivel 1) C4420 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4420
dev_langs:
- C++
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1ba4ef4c4fc006e1a5950d0d16dc530ccc06a1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049753"
---
# <a name="compiler-warning-level-1-c4420"></a>Advertencia del compilador (nivel 1) C4420

'operador': operador no disponible, utilizando 'operator' en su lugar; comprobación de tiempo de ejecución puede suponer un riesgo

Esta advertencia se genera cuando se usa el [opción /RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector comprobación new/delete) y cuando no se encuentra ningún formulario de vector. En este caso, se usa el formulario no vectorial.

Orden de la opción /RTCv funcione correctamente, el compilador siempre debe llamar a la forma vectorial de [nueva](../../cpp/new-operator-cpp.md)/[eliminar](../../cpp/delete-operator-cpp.md) si se utiliza la sintaxis de vector.