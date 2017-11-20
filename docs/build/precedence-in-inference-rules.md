---
title: Prioridad en las reglas de inferencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d22db9de1fc1941798c73c3c1c05a8ccd8571525
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="precedence-in-inference-rules"></a>Prioridad en las reglas de inferencia
Si una regla de inferencia se definió varias veces, NMAKE utiliza la definición de prioridad más alta. En la lista siguiente muestra el orden de prioridad, de mayor a menor:  
  
1.  Una regla de inferencia definida en un archivo MAKE; las definiciones posteriores tienen precedencia.  
  
2.  Una regla de inferencia definida en Tools.ini; las definiciones posteriores tienen precedencia.  
  
3.  Una regla de inferencia predefinidas.  
  
## <a name="see-also"></a>Vea también  
 [Reglas de inferencia](../build/inference-rules.md)