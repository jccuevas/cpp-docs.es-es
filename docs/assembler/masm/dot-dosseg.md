---
title: . DOSSEG | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3817cfe98758faf86ea87d74e02657598c3e806b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
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