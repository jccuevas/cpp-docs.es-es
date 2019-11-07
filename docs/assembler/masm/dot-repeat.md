---
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: 0533397c60c83f22b10c84ec72aa6eb65a71e4c0
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703565"
---
# <a name="repeat-32-bit-masm"></a>. REPEAT (de 32 bits, MASM)

Genera código que repite la ejecución del bloque de *instrucciones* hasta que `condition` sea true. [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md), que se convierte en true cuando CX es cero, se puede sustituir por [. HASTA](../../assembler/masm/dot-until.md). El `condition` es opcional con **. UNTILCXZ**. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> .REPEAT<br/>
> instrucciones<br/>
> . Condición UNTIL

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>