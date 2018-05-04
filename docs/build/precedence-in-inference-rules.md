---
title: Prioridad en las reglas de inferencia | Documentos de Microsoft
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
ms.openlocfilehash: 36d462d4222cbfc143dd7487d4cb6b1b8bb3ba3b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="precedence-in-inference-rules"></a>Prioridad en las reglas de inferencia
Si una regla de inferencia se definió varias veces, NMAKE utiliza la definición de prioridad más alta. En la lista siguiente muestra el orden de prioridad, de mayor a menor:  
  
1.  Una regla de inferencia definida en un archivo MAKE; las definiciones posteriores tienen precedencia.  
  
2.  Una regla de inferencia definida en Tools.ini; las definiciones posteriores tienen precedencia.  
  
3.  Una regla de inferencia predefinidas.  
  
## <a name="see-also"></a>Vea también  
 [Reglas de inferencia](../build/inference-rules.md)