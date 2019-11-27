---
title: .SAVEREG
ms.date: 08/30/2018
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: 324cf0e70a7ad619e5741c9acc18c24a72f54d13
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397967"
---
# <a name="savereg"></a>.SAVEREG

Genera una entrada de código de desenredado de `UWOP_SAVE_NONVOL` o `UWOP_SAVE_NONVOL_FAR` para el registro (*reg*) y el desplazamiento (*desplazamiento*) especificados mediante el desplazamiento de prólogo actual. MASM elegirá la codificación más eficaz.

## <a name="syntax"></a>Sintaxis

> **. SAVEREG** *reg* __,__ *desplazamiento*

## <a name="remarks"></a>Comentarios

**. SAVEREG**permite a los usuarios de ml64. exe especificar cómo se desenreda una función de marco y solo se permite dentro del prólogo, que se extiende desde la declaración de fotogramas de [proceso](../../assembler/masm/proc.md) a [. Directiva ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Estas directivas no generan código; solo generan `.xdata` y `.pdata`. **. SAVEREG** debe ir precedida de instrucciones que implementen realmente las acciones que se van a desenredar. Es una buena práctica encapsular las directivas de desenredado y el código que están diseñadas para desenredar en una macro para garantizar el acuerdo.

Para obtener más información, consulte [MASM para x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
