---
title: Optimizar el código ensamblador en línea | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c494594e3b7c541487f34fd33359b0e31f73dd61
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050563"
---
# <a name="optimizing-inline-assembly"></a>Optimización de un ensamblado alineado
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 La presencia de un bloque `__asm` en una función afecta a la optimización de varias maneras. En primer lugar, el compilador no intenta optimizar el propio bloque `__asm`. Lo que se escribe en el lenguaje de ensamblado es exactamente lo que se obtiene. En segundo lugar, la presencia de un bloque `__asm` afecta al almacenamiento de variables del registro. El compilador evita registrar variables a través de un bloque `__asm` si existe la posibilidad de que el bloque `__asm` cambie el contenido del registro. Por último, algunas otras optimizaciones de función resultarán afectadas por la inclusión del lenguaje de ensamblado en una función.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Ensamblador insertado](../../assembler/inline/inline-assembler.md)