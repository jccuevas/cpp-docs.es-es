---
title: . CÓDIGO | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59e376fc9c10ab8891b02e4da334341ae0534b73
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32051243"
---
# <a name="code"></a>.CODE
Cuando se utiliza con [. MODELO](../../assembler/masm/dot-model.md), indica el inicio de un segmento de código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.CODE [[name]]  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`name`|Parámetro opcional que especifica el nombre del segmento de código. El nombre predeterminado es _TEXT para pequeña y pequeño, compacto y plana [modelos](../../assembler/masm/dot-model.md). El nombre predeterminado es *modulename*_TEXT para otros modelos.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)   
 [.DATA](../../assembler/masm/dot-data.md)