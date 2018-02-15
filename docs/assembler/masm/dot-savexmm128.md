---
title: .SAVEXMM128 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .SAVEXMM128
dev_langs:
- C++
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e163f71b0c1d49f845cc871a26d4ee369843597
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="savexmm128"></a>.SAVEXMM128
Genera cualquiera una `UWOP_SAVE_XMM128` o un `UWOP_SAVE_XMM128_FAR` desenredado entrada de código para el registro de registros de XMM especificado y utilizando el desplazamiento actual del prólogo de desplazamiento. MASM elegirá la codificación más eficaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.savexmm128 xmmreg , offset  
```  
  
## <a name="remarks"></a>Comentarios  
 . Savexmm128 permite a los usuarios de ml64.exe especificar cómo se desenreda una función de marco y solo se permite en el prólogo, que abarca desde el [PROC](../../assembler/masm/proc.md) declaración de marco para el [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directiva. Estas directivas no generan código; solo generan `.xdata` y `.pdata`. . Savexmm128 debe ir precedida de instrucciones que realmente se implementan las acciones que puede desenredar. Es una buena práctica para ajustar las directivas de desenredado y el código que están concebidos para desenredar en una macro para asegurarse de acuerdo.  
  
 `offset` debe ser un múltiplo de 16.  
  
 Para obtener más información, consulte [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)