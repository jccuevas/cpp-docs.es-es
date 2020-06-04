---
title: Advertencia del compilador (nivel 3) C4723
ms.date: 11/04/2016
f1_keywords:
- C4723
helpviewer_keywords:
- C4723
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
ms.openlocfilehash: 3a47c6f7e83abfc785d602d8ee0734be5d0fa962
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174094"
---
# <a name="compiler-warning-level-3-c4723"></a>Advertencia del compilador (nivel 3) C4723

División potencial por 0

El segundo operando de una operación de división se evaluó como cero en tiempo de compilación, lo que da resultados no definidos.

Esta advertencia solo se emite cuando se usa [/og](../../build/reference/og-global-optimizations.md) o una opción de optimización que implica/OG.

Es posible que el compilador haya generado el operando cero.
