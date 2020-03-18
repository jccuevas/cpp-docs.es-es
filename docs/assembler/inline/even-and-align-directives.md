---
title: Directivas EVEN y ALIGN
ms.date: 08/30/2018
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: 63fa73988b9b9433a988035789a923ac73936214
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441584"
---
# <a name="even-and-align-directives"></a>Directivas EVEN y ALIGN

**Específicos de Microsoft**

Aunque el ensamblador alineado no admite la mayoría de las directivas MASM, admite `EVEN` y **align**. Estas directivas colocan instrucciones **NOP** (sin operación) en el código de ensamblado según sea necesario para alinear las etiquetas con límites concretos. Esto hace que las operaciones de búsqueda de instrucciones sean más eficaces en algunos procesadores.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>