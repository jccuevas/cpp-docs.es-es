---
title: ALIAS (MASM) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c1487afc250646b5cf1a12673dd43f6b1996a4f0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="alias-masm"></a>ALIAS (MASM)
El **ALIAS** directiva crea un nombre alternativo para una función.  Esto permite crear varios nombres para una función, o bibliotecas que permiten al vinculador (LINK.exe) para asignar una función antigua a una nueva función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
ALIAS  <  
alias  
> = <  
actual-name  
>  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `actual-name`  
 El nombre real de la función o procedimiento.  Son necesarios los corchetes angulares.  
  
 `alias`  
 El nombre alternativo o alias.  Son necesarios los corchetes angulares.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)