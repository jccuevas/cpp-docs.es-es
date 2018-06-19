---
title: EXTERNDEF | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b010f52f91a04388f34052fcc5c374690cff13df
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052705"
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