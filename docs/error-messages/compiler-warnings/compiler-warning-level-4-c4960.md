---
title: Advertencia del compilador (nivel 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: ff4a9b3d78a108a45abb18c22049b104e630bf15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280250"
---
# <a name="compiler-warning-level-4-c4960"></a>Advertencia del compilador (nivel 4) C4960

'function' es demasiado grande para generar un perfil

Al usar [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada con una función mayor que 65 535 instrucciones. Una función tan grande no está disponible para optimizaciones guiadas por perfil.

Para resolver esta advertencia, reduzca el tamaño de la función.