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
ms.openlocfilehash: d4956ba12e0bc268d78a895e6cb1ec6e2059262a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166885"
---
# <a name="optimizing-inline-assembly"></a>Optimización de un ensamblado alineado

**Específicos de Microsoft**

La presencia de un bloque `__asm` en una función afecta a la optimización de varias maneras. En primer lugar, el compilador no intenta optimizar el propio bloque `__asm`. Lo que se escribe en el lenguaje de ensamblado es exactamente lo que se obtiene. En segundo lugar, la presencia de un bloque `__asm` afecta al almacenamiento de variables del registro. El compilador evita registrar variables a través de un bloque `__asm` si existe la posibilidad de que el bloque `__asm` cambie el contenido del registro. Por último, algunas otras optimizaciones de función resultarán afectadas por la inclusión del lenguaje de ensamblado en una función.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>