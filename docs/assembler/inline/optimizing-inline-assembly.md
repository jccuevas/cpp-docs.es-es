---
title: "Optimizar el código ensamblador en línea | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21f6954ece6adcc60fbb3a8620dd427e7c21042a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="optimizing-inline-assembly"></a>Optimización de un ensamblado alineado
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 La presencia de un bloque `__asm` en una función afecta a la optimización de varias maneras. En primer lugar, el compilador no intenta optimizar el propio bloque `__asm`. Lo que se escribe en el lenguaje de ensamblado es exactamente lo que se obtiene. En segundo lugar, la presencia de un bloque `__asm` afecta al almacenamiento de variables del registro. El compilador evita registrar variables a través de un bloque `__asm` si existe la posibilidad de que el bloque `__asm` cambie el contenido del registro. Por último, algunas otras optimizaciones de función resultarán afectadas por la inclusión del lenguaje de ensamblado en una función.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Ensamblador insertado](../../assembler/inline/inline-assembler.md)