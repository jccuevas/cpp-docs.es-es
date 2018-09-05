---
title: . ALLOCSTACK | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .ALLOCSTACK
dev_langs:
- C++
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 292a7fcdb0a1d7c4ecccab895c643479397b4a98
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681936"
---
# <a name="allocstack"></a>.ALLOCSTACK

Genera un **UWOP_ALLOC_SMALL** o un **UWOP_ALLOC_LARGE** con el tamaño especificado para el desplazamiento actual en el prólogo.

## <a name="syntax"></a>Sintaxis

> . ALLOCSTACK tamaño

## <a name="remarks"></a>Comentarios

MASM elegirá la codificación más eficaz para un tamaño determinado.

. ALLOCSTACK permite a los usuarios ml64.exe especificar cómo se desenreda una función de marco y solo se permite en el prólogo, que se extiende desde el [PROC](../../assembler/masm/proc.md) declaración de marco para el [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directiva. Estas directivas no generan código; solo generan `.xdata` y `.pdata`. . ALLOCSTACK debe ir precedido de instrucciones que implementan las acciones que no resulte dañada. Es una buena práctica para ajustar las directivas de desenredado y el código que están diseñadas para desenredo en una macro para asegurarse de acuerdo.

El `size` operando debe ser un múltiplo de 8.

Para obtener más información, vea [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Ejemplo

El ejemplo siguiente muestra cómo especificar un controlador de excepciones y desenredo:

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

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>