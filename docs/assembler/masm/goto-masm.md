---
title: GOTO (MASM) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c86a9b5bc83110f20dccf73f51b1e1aabc693db2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="goto-masm"></a>GOTO (MASM)
Transfiere el ensamblado a la línea marcada **: *** macrolabel*.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
GOTO   
macrolabel  
  
```  
  
## <a name="remarks"></a>Comentarios  
 **GOTO** se permite solo dentro de [MACRO](../../assembler/masm/macro.md), [para](../../assembler/masm/for-masm.md), [FORC](../../assembler/masm/forc.md), [repita](../../assembler/masm/repeat.md), y **al**bloques. La etiqueta debe ser la única directiva en la línea y debe ir precedida de un signo de dos puntos inicial.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)