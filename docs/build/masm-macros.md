---
title: Macros de MASM | Documentos de Microsoft
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
ms.openlocfilehash: 403220306a2585b1506a990664eaa2ec8f2ac1a3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="masm-macros"></a>Macros de MASM
Para simplificar el uso de la [pseudoperaciones sin formato](../build/raw-pseudo-operations.md), hay un conjunto de macros, definidas en ksamd64.inc, que se puede usar para crear el procedimiento habitual prólogos y epílogos.  
  
## <a name="remarks"></a>Comentarios  
  
|Macro|Descripción|  
|-----------|-----------------|  
|alloc_stack(n)|Asigna un marco de pila de n bytes (utilizando sub rsp, n) y emite la correspondiente (.allocstack n) de la información de desenredo|  
|save_reg registro, ubicación|Guarda un registro no volátil del registro en la pila, en el desplazamiento de RSP y emite la correspondiente información de desenredo. (reg .savereg, loc)|  
|push_reg reg|Inserta un registro no volátil del registro en la pila y emite información de desenredo adecuado. (.pushreg registro)|  
|rex_push_reg registro|Guardar un registro permanente de la pila mediante una inserción de 2 bytes y emite la correspondiente información (.pushreg registro) debería usarse si la inserción es la primera instrucción de la función para asegurarse de que está estrechamente a la función de desenredo.|  
|save_xmm128 registro, ubicación|Guarda un registro XMM no variable reg en la pila, en el desplazamiento de RSP y emite la correspondiente información de desenredo (. savexmm128 registro, loc)|  
|set_frame registro, desplazamiento|Establece el registro del marco registro para ser RSP + desplazamiento (mediante mov o lea) y emite la correspondiente información de desenredo (. set_frame registro, desplazamiento)|  
|push_eflags|Inserta eflags con una instrucción pushfq y emite la correspondiente (. alloc_stack 8) de la información de desenredo|  
  
 Este es un ejemplo de prólogo de función con el uso correcto de las macros:  
  
```  
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