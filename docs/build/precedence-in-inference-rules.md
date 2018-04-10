---
title: Prioridad en las reglas de inferencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f7374da0541fc66464947af5a7b2ea7ea7b5c1d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="precedence-in-inference-rules"></a>Prioridad en las reglas de inferencia
Si una regla de inferencia se definió varias veces, NMAKE utiliza la definición de prioridad más alta. En la lista siguiente muestra el orden de prioridad, de mayor a menor:  
  
1.  Una regla de inferencia definida en un archivo MAKE; las definiciones posteriores tienen precedencia.  
  
2.  Una regla de inferencia definida en Tools.ini; las definiciones posteriores tienen precedencia.  
  
3.  Una regla de inferencia predefinidas.  
  
## <a name="see-also"></a>Vea también  
 [Reglas de inferencia](../build/inference-rules.md)