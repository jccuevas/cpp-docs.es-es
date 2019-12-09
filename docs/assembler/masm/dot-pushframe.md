---
title: .PUSHFRAME
description: Describe la. PUSHFRAME MASM Directive, que se usa para especificar cómo desenredar una función de marco.
ms.date: 12/06/2019
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 5f951396291ecb12dab500a364f176106c5daa8b
ms.sourcegitcommit: 2cac0150ab3bc8260f866451019b8e22c7e1ac11
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2019
ms.locfileid: "74945857"
---
# <a name="pushframe"></a>.PUSHFRAME

Genera una entrada de código de desenredado de `UWOP_PUSH_MACHFRAME`. Si se especifica la palabra clave de **código** opcional, se asigna a la entrada de código de desenredado el modificador 1. De lo contrario, el modificador es 0.

## <a name="syntax"></a>Sintaxis

> **. PUSHFRAME** ⟦**code**⟧;;

## <a name="remarks"></a>Notas

. PUSHFRAME permite a los usuarios de ml64. exe especificar cómo se desenreda una función de marco. Solo se permite dentro del prólogo, que se extiende desde la declaración de marco de [proceso](../../assembler/masm/proc.md) hasta [. Directiva ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Estas directivas no generan código; solo generan `.xdata` y `.pdata`. **. PUSHFRAME** debe ir precedida de instrucciones que implementen realmente las acciones que se van a desenredar. Es una buena práctica encapsular las directivas de desenredado y el código que están diseñadas para desenredar en una macro para garantizar el acuerdo.

Para obtener más información, consulte [MASM para x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
