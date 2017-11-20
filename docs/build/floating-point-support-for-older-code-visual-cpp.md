---
title: "Compatibilidad de punto flotante para el código anterior (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3ddc151a2a0f74c6f77be68cd026147a318a595a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="floating-point-support-for-older-code-visual-c"></a>Compatibilidad del código antiguo con puntos flotantes (Visual C++)
Los registros MMX y pila de punto flotante (MM0-MM7/ST0-ST7) se conservan en cambios de contexto.  No hay ninguna convención de llamada explícita para estos registros.  El uso de estos registros está estrictamente prohibido en código en modo kernel.  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)