---
title: COMM | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 111dac47089fea13febe787e5b73557b287beea8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="comm"></a>COMM
Crea una variable comunes con los atributos especificados en `definition`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## <a name="remarks"></a>Comentarios  
 Cada `definition` tiene la forma siguiente:  
  
 [[*langtype*]] [[**NEAR** &#124; **lejano**]] *etiqueta ***:**`type`[[**:*** recuento*]]  
  
 El *etiqueta* es el nombre de la variable. El `type` puede ser cualquier especificador de tipo ([bytes](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md), y así sucesivamente) o un entero que especifica el número de bytes. El *recuento* especifica el número de objetos de datos (uno es el valor predeterminado).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)