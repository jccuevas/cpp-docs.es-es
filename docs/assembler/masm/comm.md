---
title: COMM | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6258a584d39f598b32c43affc0ef2569b77b2047
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="comm"></a>COMM
Crea una variable comunes con los atributos especificados en `definition`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## <a name="remarks"></a>Comentarios  
 Cada `definition` tiene la forma siguiente:  
  
 [[*langtype*]] [[**NEAR** &#124; **Lejano**]] *etiqueta***:**`type`[[**:***recuento*]]  
  
 El *etiqueta* es el nombre de la variable. El `type` puede ser cualquier especificador de tipo ([bytes](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md), y así sucesivamente) o un entero que especifica el número de bytes. El *recuento* especifica el número de objetos de datos (uno es el valor predeterminado).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)