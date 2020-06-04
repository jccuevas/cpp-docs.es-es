---
title: Advertencia del compilador (nivel 3) C4023
ms.date: 11/04/2016
f1_keywords:
- C4023
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
ms.openlocfilehash: ed24c48b4054aacf673b031ebc05409a5c3e91dd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161612"
---
# <a name="compiler-warning-level-3-c4023"></a>Advertencia del compilador (nivel 3) C4023

'símbolo': el puntero con base se pasó a la función sin prototipo: número de parámetro

Si se pasa un puntero con base a una función sin prototipo, el puntero se normaliza, con resultados imprevisibles.

Para resolver esta advertencia, use funciones prototipo a las que se pasan punteros con base.
