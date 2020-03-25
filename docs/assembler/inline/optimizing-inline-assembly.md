---
title: Optimización de un ensamblado alineado
ms.date: 08/30/2018
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
ms.openlocfilehash: 0051b16ddc19e233cfac2688c0b77e1e023f0833
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169271"
---
# <a name="optimizing-inline-assembly"></a>Optimización de un ensamblado alineado

**Específicos de Microsoft**

La presencia de un bloque `__asm` en una función afecta a la optimización de varias maneras. En primer lugar, el compilador no intenta optimizar el propio bloque `__asm`. Lo que se escribe en el lenguaje de ensamblado es exactamente lo que se obtiene. En segundo lugar, la presencia de un bloque `__asm` afecta al almacenamiento de variables del registro. El compilador evita registrar variables a través de un bloque `__asm` si existe la posibilidad de que el bloque `__asm` cambie el contenido del registro. Por último, algunas otras optimizaciones de función resultarán afectadas por la inclusión del lenguaje de ensamblado en una función.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>
