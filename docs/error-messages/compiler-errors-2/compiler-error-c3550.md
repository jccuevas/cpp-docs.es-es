---
title: Error del compilador C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 17c90aa68b29c9490deb8d49895162e8a6bdefec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200777"
---
# <a name="compiler-error-c3550"></a>Error del compilador C3550

solo se permite 'decltype(auto)' sin formato en este contexto

Si se usa `decltype(auto)` como marcador de posición para el tipo de valor devuelto de una función, debe usarse por sí mismo. No se puede usar como parte de una declaración de puntero (`decltype(auto*)`), una declaración de referencia (`decltype(auto&)`) o cualquier otra cualificación similar.

## <a name="see-also"></a>Consulte también

[auto](../../cpp/auto-cpp.md)
