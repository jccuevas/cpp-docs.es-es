---
title: GOTO (MASM) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9eecdab2fe91de0aae656b37c6fddafe658e60c0
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
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