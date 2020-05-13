---
title: Advertencia del compilador (nivel 1) C4182
ms.date: 11/04/2016
f1_keywords:
- C4182
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
ms.openlocfilehash: a438373b7fda04a6e8d1f76e2ef38208c3e557a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175953"
---
# <a name="compiler-warning-level-1-c4182"></a>Advertencia del compilador (nivel 1) C4182

\#incluir el nivel de anidamiento es "número" profundo; posible recursividad infinita

El compilador se quedó sin espacio en el montón debido al número de archivos de inclusión anidados. Un archivo de inclusión está anidado cuando se incluye desde otro archivo de inclusión.

Este mensaje es informativo y precede al error [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md).
