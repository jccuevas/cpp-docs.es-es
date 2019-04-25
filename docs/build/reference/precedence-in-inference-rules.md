---
title: Prioridad en las reglas de inferencia
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: ca24134fd1829ad3d97ca67b8c30aae3af4109ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319686"
---
# <a name="precedence-in-inference-rules"></a>Prioridad en las reglas de inferencia

Si se definió una regla de inferencia, NMAKE utiliza la definición de la prioridad más alta. En la lista siguiente se muestra el orden de prioridad de mayor a menor:

1. Regla de inferencia definida en un archivo MAKE; las definiciones posteriores tienen la prioridad.

1. Una regla de inferencia definida en Tools.ini; las definiciones posteriores tienen la prioridad.

1. Una regla de inferencia predefinidas.

## <a name="see-also"></a>Vea también

[Reglas de inferencia](inference-rules.md)
