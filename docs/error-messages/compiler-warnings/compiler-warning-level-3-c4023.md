---
title: Advertencia del compilador (nivel 3) C4023
ms.date: 11/04/2016
f1_keywords:
- C4023
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
ms.openlocfilehash: 4d433ff7d6b323fcb8508872d4e755f893a50f5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402364"
---
# <a name="compiler-warning-level-3-c4023"></a>Advertencia del compilador (nivel 3) C4023

'símbolo': el puntero con base se pasó a la función sin prototipo: número de parámetro

Si se pasa un puntero con base a una función sin prototipo, el puntero se normaliza, con resultados imprevisibles.

Para resolver esta advertencia, use funciones prototipo a las que se pasan punteros con base.