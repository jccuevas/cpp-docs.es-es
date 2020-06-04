---
title: .PUSHREG
ms.date: 12/16/2019
f1_keywords:
- .PUSHREG
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
ms.openlocfilehash: de6ffd3668f47732144e8c632410f6dfde6b2f31
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318298"
---
# <a name="pushreg"></a>.PUSHREG

Genera una entrada de código de desenredado de `UWOP_PUSH_NONVOL` para el número de registro especificado utilizando el desplazamiento actual en el prólogo.

## <a name="syntax"></a>Sintaxis

> . *Registro* de PUSHREG

## <a name="remarks"></a>Notas

**. PUSHREG** permite a los usuarios de ml64. exe especificar cómo se desenreda una función de marco y solo se permite dentro del prólogo, que se extiende desde la declaración de **fotogramas** de [proceso](proc.md) a [. Directiva ENDPROLOG](dot-endprolog.md) . Estas directivas no generan código; solo generan `.xdata` y `.pdata`. **. PUSHREG** debe ir precedida de instrucciones que implementen realmente las acciones que se van a desenredar. Es una buena práctica encapsular las directivas de desenredado y el código que están diseñadas para desenredar en una macro para garantizar el acuerdo.

*el registro* puede ser uno de: \
RAX | RCX | RDX | RBX | RDI | RSI | RBP | R8 | R9 | R10 | R11 | R12 | R13 | R14 | R15.

Para obtener más información, consulte [MASM para x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo siguiente se muestra cómo se envían registros no volátiles.

### <a name="code"></a>Código

```asm
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE
_text SEGMENT
Example1 PROC FRAME
   push r10
.pushreg r10
   push r15
.pushreg r15
   push rbx
.pushreg rbx
   push rsi
.pushreg rsi
.endprolog
   ; rest of function ...
   ret
Example1 ENDP
_text ENDS
END
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
