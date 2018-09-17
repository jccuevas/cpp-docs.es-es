---
title: Prioridad en las reglas de inferencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4f2e7ff55e935b7e425b552ba85f47f134c6b80
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725236"
---
# <a name="precedence-in-inference-rules"></a>Prioridad en las reglas de inferencia

Si se definió una regla de inferencia, NMAKE utiliza la definición de la prioridad más alta. En la lista siguiente se muestra el orden de prioridad de mayor a menor:

1. Regla de inferencia definida en un archivo MAKE; las definiciones posteriores tienen la prioridad.

1. Una regla de inferencia definida en Tools.ini; las definiciones posteriores tienen la prioridad.

1. Una regla de inferencia predefinidas.

## <a name="see-also"></a>Vea también

[Reglas de inferencia](../build/inference-rules.md)