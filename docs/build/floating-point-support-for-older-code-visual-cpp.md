---
title: Compatibilidad de punto flotante para el código anterior (Visual C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd7cbf955fbf795d06d9cd2448d0736dc435f3b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="floating-point-support-for-older-code-visual-c"></a>Compatibilidad del código antiguo con puntos flotantes (Visual C++)
Los registros MMX y pila de punto flotante (MM0-MM7/ST0-ST7) se conservan en cambios de contexto.  No hay ninguna convención de llamada explícita para estos registros.  El uso de estos registros está estrictamente prohibido en código en modo kernel.  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)