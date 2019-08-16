---
title: .SETFRAME
ms.date: 08/30/2018
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: c2c35cdb2889350b27e9fb11c397b684506972c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178181"
---
# <a name="setframe"></a>.SETFRAME

Rellenos en el marco de registrar el campo y el desplazamiento en la información de desenredo mediante el registro especificado (`reg`) y el desplazamiento (`offset`). El desplazamiento debe ser un múltiplo de 16 y menor o igual a 240. Esta directiva también genera un `UWOP_SET_FPREG` entrada de código de desenredo para registrar el texto especificado utilizando el desplazamiento actual del prólogo.

## <a name="syntax"></a>Sintaxis

> . SETFRAME registro, desplazamiento

## <a name="remarks"></a>Comentarios

. SETFRAME permite a los usuarios de ml64.exe especificar cómo se desenreda una función de marco y solo se permite en el prólogo, que se extiende desde el [PROC](../../assembler/masm/proc.md) declaración de marco para el [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directiva. Estas directivas no generan código; solo generan `.xdata` y `.pdata`. . SETFRAME debe ir precedido de instrucciones que implementan las acciones que no resulte dañada. Es una buena práctica para ajustar las directivas de desenredado y el código que están diseñadas para desenredo en una macro para asegurarse de acuerdo.

Para obtener más información, consulte [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Ejemplo

### <a name="description"></a>Descripción

El ejemplo siguiente muestra cómo usar un puntero de marco:

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

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>