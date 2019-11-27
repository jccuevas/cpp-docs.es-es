---
title: .PUSHFRAME
ms.date: 08/30/2018
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: b0f047278f6250d5ef359f7992df4ea23f4bbd9b
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398043"
---
# <a name="pushframe"></a>.PUSHFRAME

Genera una entrada de código de desenredado de `UWOP_PUSH_MACHFRAME`. Si se especifica el *código* opcional, se asigna a la entrada de código de desenredado el modificador 1. De lo contrario, el modificador es 0.

## <a name="syntax"></a>Sintaxis

> **. PUSHFRAME** ⟦*code*⟧;;

## <a name="remarks"></a>Comentarios

. PUSHFRAME permite a los usuarios de ml64. exe especificar cómo se desenreda una función de marco y solo se permite dentro del prólogo, que se extiende desde la declaración de fotogramas de [proceso](../../assembler/masm/proc.md) a [. Directiva ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Estas directivas no generan código; solo generan `.xdata` y `.pdata`. **. PUSHFRAME** debe ir precedida de instrucciones que implementen realmente las acciones que se van a desenredar. Es una buena práctica encapsular las directivas de desenredado y el código que están diseñadas para desenredar en una macro para garantizar el acuerdo.

Para obtener más información, consulte [MASM para x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
