---
title: Directivas EVEN y ALIGN
ms.date: 08/30/2018
f1_keywords:
- align
- EVEN
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: 522d5689d680d0fc334743d2802abe21570dd6f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167324"
---
# <a name="even-and-align-directives"></a>Directivas EVEN y ALIGN

**Específicos de Microsoft**

Aunque el ensamblador alineado no admite la mayoría de las directivas MASM, es compatible con `EVEN` y **alinear**. Estas directivas colocan **NOP** (sin operación) instrucciones que aparecen en el código de ensamblado según sea necesario para ajustar las etiquetas a los límites específicos. Esto hace que las operaciones de búsqueda de instrucciones sean más eficaces en algunos procesadores.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>