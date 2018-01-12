---
title: . SAVEXMM128 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .SAVEXMM128
dev_langs: C++
helpviewer_keywords: .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 384615a0c58c3c28a2e0958d6909546f5753ce6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="savexmm128"></a>.SAVEXMM128
Genera cualquiera una `UWOP_SAVE_XMM128` o un `UWOP_SAVE_XMM128_FAR` desenredado entrada de código para el registro de registros de XMM especificado y utilizando el desplazamiento actual del prólogo de desplazamiento. MASM elegirá la codificación más eficaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.savexmm128 xmmreg , offset  
```  
  
## <a name="remarks"></a>Comentarios  
 . Savexmm128 permite a los usuarios de ml64.exe especificar cómo se desenreda una función de marco y solo se permite en el prólogo, que abarca desde el [PROC](../../assembler/masm/proc.md) declaración de marco para el [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directiva. Estas directivas no generan código; solo generan `.xdata` y `.pdata`. . Savexmm128 debe ir precedida de instrucciones que realmente se implementan las acciones que puede desenredar. Es una buena práctica para ajustar las directivas de desenredado y el código que están concebidos para desenredar en una macro para asegurarse de acuerdo.  
  
 `offset`debe ser un múltiplo de 16.  
  
 Para obtener más información, consulte [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)