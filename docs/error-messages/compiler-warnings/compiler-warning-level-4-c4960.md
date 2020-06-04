---
title: Advertencia del compilador (nivel 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: 286d3a1953c6c6badf15b712feac99afafe8b0a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198125"
---
# <a name="compiler-warning-level-4-c4960"></a>Advertencia del compilador (nivel 4) C4960

'function' es demasiado grande para generar un perfil

Al usar [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada con una función mayor que 65 535 instrucciones. Una función tan grande no está disponible para optimizaciones guiadas por perfil.

Para resolver esta advertencia, reduzca el tamaño de la función.
