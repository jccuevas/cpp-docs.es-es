---
title: EXTERN (MASM) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: extern
dev_langs: C++
helpviewer_keywords: EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 814922100d34534d51abed4cb682cc4181685066
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="extern-masm"></a>EXTERN (MASM)
Define una o más variables externas, etiquetas o símbolos que se denominan *nombre* cuyo tipo es `type`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
   EXTERN [[langtype]] name [[(altid)]] :  
type [[, [[langtype]] name [[(altid)]] :type]]...  
```  
  
## <a name="remarks"></a>Comentarios  
 El `type` puede ser [ABS](../../assembler/masm/operator-abs.md), que importa *nombre* como una constante. Igual que [EXTRN](../../assembler/masm/extrn.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)