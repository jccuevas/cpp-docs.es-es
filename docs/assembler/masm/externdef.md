---
title: EXTERNDEF | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a463f4f74f380c6d927419eb498ccd868587ac6d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="externdef"></a>EXTERNDEF
Define una o más variables externas, etiquetas o símbolos que se denominan *nombre* cuyo tipo es `type`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
EXTERNDEF [[langtype]] name:type [[, [[langtype]] name:type]]...  
```  
  
## <a name="remarks"></a>Comentarios  
 Si *nombre* se define en el módulo, se trata como [público](../../assembler/masm/public-masm.md). Si *nombre* se hace referencia en el módulo, se trata como [EXTERN](../../assembler/masm/extern-masm.md). Si *nombre* no es hace referencia, se omite. El `type` puede ser [ABS](../../assembler/masm/operator-abs.md), que importa *nombre* como una constante. Se utiliza normalmente en archivos de inclusión.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)