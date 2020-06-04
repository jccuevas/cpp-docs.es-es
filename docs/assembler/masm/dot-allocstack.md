---
title: .ALLOCSTACK
ms.date: 12/17/2019
f1_keywords:
- .ALLOCSTACK
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
ms.openlocfilehash: bcc94619dfa24ab5c8b5d23a60825641290ef176
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75314190"
---
# <a name="allocstack"></a>.ALLOCSTACK

Genera un **UWOP_ALLOC_SMALL** o un **UWOP_ALLOC_LARGE** con el tamaño especificado para el desplazamiento actual en el prólogo.

## <a name="syntax"></a>Sintaxis

> **.**  *Tamaño* de ALLOCSTACK

## <a name="remarks"></a>Notas

MASM elegirá la codificación más eficaz para un tamaño determinado.

**. ALLOCSTACK** permite a los usuarios de ml64. exe especificar cómo se desenreda una función de marco y solo se permite dentro del prólogo, que se extiende desde la declaración de fotogramas de [proceso](proc.md) a [. Directiva ENDPROLOG](dot-endprolog.md) . Estas directivas no generan código; solo generan `.xdata` y `.pdata`. **. ALLOCSTACK** debe ir precedida de instrucciones que implementen realmente las acciones que se van a desenredar. Es una buena práctica encapsular las directivas de desenredado y el código que están diseñadas para desenredar en una macro para garantizar el acuerdo.

El operando de *tamaño* debe ser un múltiplo de 8.

Para obtener más información, consulte [MASM para x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Ejemplo

En el ejemplo siguiente se muestra cómo especificar un controlador de desenredo/excepción:

```asm
; ml64 ex3.asm /link /entry:Example1  /SUBSYSTEM:Console
text SEGMENT
PUBLIC Example3
PUBLIC Example3_UW
Example3_UW PROC NEAR
   ; exception/unwind handler body

   ret 0

Example3_UW ENDP

Example3 PROC FRAME : Example3_UW

   sub rsp, 16
.allocstack 16

.endprolog

   ; function body
    add rsp, 16
   ret 0

Example3 ENDP
text ENDS
END
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
