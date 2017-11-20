---
title: . SETFRAME | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .SETFRAME
dev_langs: C++
helpviewer_keywords: .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8666e0ecfd1b2f81236766a1a32baea7a939cd19
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="setframe"></a>.SETFRAME
Rellenos en el marco de registrar el campo y el desplazamiento en la información de desenredo mediante el registro especificado (`reg`) y el desplazamiento (`offset`). El desplazamiento debe ser un múltiplo de 16 y menor o igual que 240. Esta directiva también genera una `UWOP_SET_FPREG` entrada al código de desenredo para registra especificado utilizando el desplazamiento actual del prólogo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.SETFRAME reg, offset  
```  
  
## <a name="remarks"></a>Comentarios  
 . SETFRAME permite a los usuarios de ml64.exe especificar cómo se desenreda una función de marco y solo se permite en el prólogo, que abarca desde el [PROC](../../assembler/masm/proc.md) declaración de marco para el [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directiva. Estas directivas no generan código; solo generan `.xdata` y `.pdata`. . SETFRAME debe ir precedida de instrucciones que realmente se implementan las acciones que puede desenredar. Es una buena práctica para ajustar las directivas de desenredado y el código que están concebidos para desenredar en una macro para asegurarse de acuerdo.  
  
 Para obtener más información, consulte [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="sample"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 El ejemplo siguiente muestra cómo utilizar un puntero de marco:  
  
### <a name="code"></a>Código  
  
```  
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
 [Referencia de directivas](../../assembler/masm/directives-reference.md)