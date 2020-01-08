---
title: .SAVEREG
ms.date: 12/16/2019
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: 18cb6e563084e8c5357bec2a8052a2b38fcdffee
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317557"
---
# <a name="savereg"></a>.SAVEREG

Genera una entrada de código de desenredado de `UWOP_SAVE_NONVOL` o `UWOP_SAVE_NONVOL_FAR` para el registro (*reg*) y el desplazamiento (*desplazamiento*) especificados mediante el desplazamiento de prólogo actual. MASM elegirá la codificación más eficaz.

## <a name="syntax"></a>Sintaxis

> **. SAVEREG** *reg* __,__ *desplazamiento*

## <a name="remarks"></a>Notas

**. SAVEREG** permite a los usuarios de ml64. exe especificar cómo se desenreda una función de marco y solo se permite dentro del prólogo, que se extiende desde la declaración de fotogramas de [proceso](proc.md) a [. Directiva ENDPROLOG](dot-endprolog.md) . Estas directivas no generan código; solo generan `.xdata` y `.pdata`. **. SAVEREG** debe ir precedida de instrucciones que implementen realmente las acciones que se van a desenredar. Es una buena práctica encapsular las directivas de desenredado y el código que están diseñadas para desenredar en una macro para garantizar el acuerdo.

Para obtener más información, consulte [MASM para x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
