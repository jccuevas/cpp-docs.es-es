---
title: Advertencia del compilador (nivel 1) C4729
ms.date: 11/04/2016
f1_keywords:
- C4729
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
ms.openlocfilehash: e78606f117251fa8ab1f08f2cef280a266309c32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185833"
---
# <a name="compiler-warning-level-1-c4729"></a>Advertencia del compilador (nivel 1) C4729

función demasiado grande para advertencias basadas en gráficos de flujos

Esta advertencia se genera cuando una función es demasiado grande para compilarse con una comprobación confiable en situaciones que generarían una advertencia. Esta advertencia solo se genera cuando se utiliza la opción del compilador [/Od](../../build/reference/od-disable-debug.md) .

Para resolver esta advertencia, divida la función en funciones más pequeñas.
