---
title: Advertencia del compilador (nivel 3) C4723
ms.date: 11/04/2016
f1_keywords:
- C4723
helpviewer_keywords:
- C4723
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
ms.openlocfilehash: b970c9ee02339fa3b48135d321638db7e64baf82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401623"
---
# <a name="compiler-warning-level-3-c4723"></a>Advertencia del compilador (nivel 3) C4723

posible división por 0

El segundo operando en una operación de división que se evalúa como cero en tiempo de compilación, dando resultados no definidos.

Esta advertencia se emite cuando se usa [/Og](../../build/reference/og-global-optimizations.md) o una opción de optimización que implique/Og.

Puede que el compilador ha generado el operando cero.