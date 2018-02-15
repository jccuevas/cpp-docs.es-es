---
title: .CODE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: de0a9b8930c04929b05b02931a1f796d28a78099
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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