---
title: ALIAS (MASM) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b14e1c41a448d0cb7014dabc50a42305249938f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
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