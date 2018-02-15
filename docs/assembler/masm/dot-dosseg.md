---
title: .DOSSEG | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 39f02937ed1613cbd759621b2a4e75f84db918cf
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="dosseg"></a>.DOSSEG
Ordena los segmentos según la convención de segmento de MS-DOS: código en primer lugar, segmentos, a continuación, no en DGROUP y, a continuación, segmentos en DGROUP.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.DOSSEG  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Los segmentos DGROUP siguen este orden: segmentos no BSS o pila, a continuación, segmentos BSS y, finalmente, segmentos de pila. Se utiliza principalmente para garantizar la compatibilidad de CodeView en programas independientes de MASM. Igual que [DOSSEG](../../assembler/masm/dosseg.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)