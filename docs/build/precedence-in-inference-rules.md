---
title: Prioridad en las reglas de inferencia
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: 30dee54c99115c076f7662bafb8aa22d97f234fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548738"
---
# <a name="precedence-in-inference-rules"></a>Prioridad en las reglas de inferencia

Si se definió una regla de inferencia, NMAKE utiliza la definición de la prioridad más alta. En la lista siguiente se muestra el orden de prioridad de mayor a menor:

1. Regla de inferencia definida en un archivo MAKE; las definiciones posteriores tienen la prioridad.

1. Una regla de inferencia definida en Tools.ini; las definiciones posteriores tienen la prioridad.

1. Una regla de inferencia predefinidas.

## <a name="see-also"></a>Vea también

[Reglas de inferencia](../build/inference-rules.md)