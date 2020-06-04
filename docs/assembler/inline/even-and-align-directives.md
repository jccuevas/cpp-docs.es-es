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
ms.openlocfilehash: b191ce0942d7596090bfd7948a37a5c9e6aac15e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169440"
---
# <a name="even-and-align-directives"></a>Directivas EVEN y ALIGN

**Específicos de Microsoft**

Aunque el ensamblador alineado no admite la mayoría de las directivas MASM, admite `EVEN` y **align**. Estas directivas colocan instrucciones **NOP** (sin operación) en el código de ensamblado según sea necesario para alinear las etiquetas con límites concretos. Esto hace que las operaciones de búsqueda de instrucciones sean más eficaces en algunos procesadores.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
