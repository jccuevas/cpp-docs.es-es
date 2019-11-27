---
title: .SETFRAME
ms.date: 08/30/2018
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: a21dda496d32abcfeb4692d0228afdbcfd4e5ebb
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397929"
---
# <a name="setframe"></a>.SETFRAME

Rellena el campo de registro de marco y el desplazamiento en la información de desenredado mediante el registro especificado (*reg*) y el desplazamiento (*desplazamiento*). El desplazamiento debe ser un múltiplo de 16 y menor o igual que 240. Esta Directiva también genera una entrada de código de desenredado de `UWOP_SET_FPREG` para el registro especificado mediante el desplazamiento de prólogo actual.

## <a name="syntax"></a>Sintaxis

> **. SETFRAME** *reg*, *desplazamiento*

## <a name="remarks"></a>Comentarios

**. SETFRAME** permite a los usuarios de ml64. exe especificar cómo se desenreda una función de marco y solo se permite dentro del prólogo, que se extiende desde la declaración de fotogramas de [proceso](../../assembler/masm/proc.md) a [. Directiva ENDPROLOG](../../assembler/masm/dot-endprolog.md) . Estas directivas no generan código; solo generan `.xdata` y `.pdata`. **. SETFRAME** debe ir precedida de instrucciones que implementen realmente las acciones que se van a desenredar. Es una buena práctica encapsular las directivas de desenredado y el código que están diseñadas para desenredar en una macro para garantizar el acuerdo.

Para obtener más información, consulte [MASM para x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo siguiente se muestra cómo usar un puntero de marco:

### <a name="code"></a>Código

```asm
; ml64 frmex2.asm /link /entry:frmex2 /SUBSYSTEM:CONSOLE
_text SEGMENT
frmex2 PROC FRAME
   push rbp
.pushreg rbp
   sub rsp, 010h
.allocstack 010h
   mov rbp, rsp
.setframe rbp, 0
.endprolog
   ; modify the stack pointer outside of the prologue (similar to alloca)
   sub rsp, 060h

   ; we can unwind from the following AV because of the frame pointer
   mov rax, 0
   mov rax, [rax] ; AV!

   add rsp, 060h
   add rsp, 010h
   pop rbp
   ret
frmex2 ENDP
_text ENDS
END
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
