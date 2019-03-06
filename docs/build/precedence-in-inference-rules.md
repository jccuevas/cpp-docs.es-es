---
title: Prioridad en las reglas de inferencia
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: 99d92985b00f7c05f409b43009eb61cec6d6f1b1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413283"
---
# <a name="precedence-in-inference-rules"></a>Prioridad en las reglas de inferencia

Si se definió una regla de inferencia, NMAKE utiliza la definición de la prioridad más alta. En la lista siguiente se muestra el orden de prioridad de mayor a menor:

1. Regla de inferencia definida en un archivo MAKE; las definiciones posteriores tienen la prioridad.

1. Una regla de inferencia definida en Tools.ini; las definiciones posteriores tienen la prioridad.

1. Una regla de inferencia predefinidas.

## <a name="see-also"></a>Vea también

[Reglas de inferencia](../build/inference-rules.md)
