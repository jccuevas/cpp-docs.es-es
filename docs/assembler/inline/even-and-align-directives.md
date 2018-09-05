---
title: Directivas EVEN y ALIGN | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- align
- EVEN
dev_langs:
- C++
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06a1007c50e3490e5b14e4da886494557be0d37e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688306"
---
# <a name="even-and-align-directives"></a>Directivas EVEN y ALIGN

**Específicos de Microsoft**

Aunque el ensamblador alineado no admite la mayoría de las directivas MASM, es compatible con `EVEN` y **alinear**. Estas directivas colocan **NOP** (sin operación) instrucciones que aparecen en el código de ensamblado según sea necesario para ajustar las etiquetas a los límites específicos. Esto hace que las operaciones de búsqueda de instrucciones sean más eficaces en algunos procesadores.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>