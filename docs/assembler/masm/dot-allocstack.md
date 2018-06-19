---
title: . ALLOCSTACK | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 00fd3028a38ff33edf7a721d2efb57fc3581152c
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050872"
---
# <a name="allocstack"></a>.ALLOCSTACK
Genera un **UWOP_ALLOC_SMALL** o un **UWOP_ALLOC_LARGE** con el tamaño especificado para el desplazamiento actual en el prólogo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.ALLOCSTACK size  
```  
  
## <a name="remarks"></a>Comentarios  
 MASM elegirá la codificación más eficaz para un tamaño determinado.  
  
 . ALLOCSTACK permite a los usuarios ml64.exe especificar cómo se desenreda una función de marco y solo se permite en el prólogo, que abarca desde el [PROC](../../assembler/masm/proc.md) declaración de marco para el [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directiva. Estas directivas no generan código; solo generan `.xdata` y `.pdata`. . ALLOCSTACK debe ir precedida de instrucciones que realmente se implementan las acciones que puede desenredar. Es una buena práctica para ajustar las directivas de desenredado y el código que están concebidos para desenredar en una macro para asegurarse de acuerdo.  
  
 El `size` operando debe ser un múltiplo de 8.  
  
 Para obtener más información, vea [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="sample"></a>Ejemplo  
 El ejemplo siguiente muestra cómo especificar un controlador de excepciones/desenredo:  
  
```  
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
 [Referencia de directivas](../../assembler/masm/directives-reference.md)