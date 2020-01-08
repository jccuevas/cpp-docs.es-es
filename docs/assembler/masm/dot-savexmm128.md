---
title: .SAVEXMM128
ms.date: 12/17/2019
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: 6402b75c10b1400d56923116621f00b4d0908822
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318259"
---
# <a name="savexmm128"></a>.SAVEXMM128

Genera una entrada de código de desenredado de `UWOP_SAVE_XMM128` o `UWOP_SAVE_XMM128_FAR` para el registro de XMM y el desplazamiento especificados utilizando el desplazamiento de prólogo actual. MASM elegirá la codificación más eficaz.

## <a name="syntax"></a>Sintaxis

> **. SAVEXMM128** *xmmreg* , *desplazamiento*

## <a name="remarks"></a>Notas

**. SAVEXMM128** permite a los usuarios de ml64. exe especificar cómo se desenreda una función de marco y solo se permite dentro del prólogo, que se extiende desde la declaración de fotogramas de [proceso](proc.md) a [. Directiva ENDPROLOG](dot-endprolog.md) . Estas directivas no generan código; solo generan `.xdata` y `.pdata`. . SAVEXMM128 debe ir precedida de instrucciones que implementen realmente las acciones que se van a desenredar. Es una buena práctica encapsular las directivas de desenredado y el código que están diseñadas para desenredar en una macro para garantizar el acuerdo.

el *desplazamiento* debe ser un múltiplo de 16.

Para obtener más información, consulte [MASM para x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
