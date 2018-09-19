---
title: Macros de MASM | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb436acae117c78bfa5c752b905bd3f4f910e9da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707855"
---
# <a name="masm-macros"></a>Macros de MASM

Con el fin de simplificar el uso de la [pseudoperaciones sin formato](../build/raw-pseudo-operations.md), hay un conjunto de macros, definidas en ksamd64.inc, que puede usarse para crear un procedimiento típico prólogos y epílogos.

## <a name="remarks"></a>Comentarios

|Macro|Descripción|
|-----------|-----------------|
|alloc_stack(n)|Asigna un marco de pila de n bytes (utilizando sub rsp, n) y emite adecuado (.allocstack n) de la información de desenredo|
|save_reg registro, ubicación|Guarda un registro permanente del registro de la pila en el desplazamiento de RSP y emite información de desenredo adecuado. (reg .savereg, loc)|
|reg push_reg|Inserta un registro permanente del registro en la pila y emite información de desenredo adecuado. (.pushreg registro)|
|rex_push_reg registro|Guardar un registro permanente de la pila mediante una inserción de 2 bytes y emite información (.pushreg registro) se debe usar si la inserción es la primera instrucción en la función para asegurarse de que la función es "n" patchable de desenredo adecuado.|
|save_xmm128 registro, ubicación|Guarda un registro XMM no variable de registro de la pila en el desplazamiento de RSP y emite la correspondiente información de desenredo (reg. savexmm128, loc)|
|registro set_frame, desplazamiento|Establece el marco registro del registro para ser RSP + desplazamiento (mediante mov o lea) y emite la correspondiente información de desenredo (reg. set_frame, desplazamiento)|
|push_eflags|Inserta eflags con una instrucción pushfq y emite adecuado (. alloc_stack 8) de la información de desenredo|

Este es un ejemplo de prólogo de función con el uso correcto de las macros:

```asm
SkFrame struct
Fill    dq ?; fill to 8 mod 16
SavedRdi dq ?; saved register RDI
SavedRsi dq ?; saved register RSI
SkFrame ends

sampleFrame struct
Filldq?; fill to 8 mod 16
SavedRdidq?; Saved Register RDI
SavedRsi  dq?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
alloc_stack(sizeof sampleFrame)
save_reg rdi, sampleFrame.SavedRdi
save_reg rsi, sampleFrame.SavedRsi
.end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here’s the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="see-also"></a>Vea también

[Aplicaciones auxiliares de desenredo para MASM](../build/unwind-helpers-for-masm.md)