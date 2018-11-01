---
title: Error del compilador C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: dbed14b9f2fa0f2163484edd8b5dfa330af9cbf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498892"
---
# <a name="compiler-error-c3550"></a>Error del compilador C3550

solo se permite 'decltype(auto)' sin formato en este contexto

Si se usa `decltype(auto)` como marcador de posición para el tipo de valor devuelto de una función, debe usarse por sí mismo. No se puede usar como parte de una declaración de puntero (`decltype(auto*)`), una declaración de referencia (`decltype(auto&)`) o cualquier otra cualificación similar.

## <a name="see-also"></a>Vea también

[auto](../../cpp/auto-cpp.md)