---
title: UNIÓN | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- union
dev_langs:
- C++
helpviewer_keywords:
- UNION directive
ms.assetid: 52504abf-7dc1-47c5-944c-b886803a0c6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71a2d7644e14903d2c4a9c4191ce54c8fea14849
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="union"></a>UNION
Declara una unión de uno o más tipos de datos. El *fielddeclarations* debe ser definiciones de datos válido. Omitir la [finaliza](../../assembler/masm/ends-masm.md) *nombre* etiqueta anidada **UNION** definiciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      name   
      UNION [[alignment]] [[, NONUNIQUE]]  
   fielddeclarations  
[[name]] ENDS  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)