---
title: INCLUIR (MASM) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- include
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE directive
ms.assetid: 1c7964ee-715c-414e-a45e-74af93476eb4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 346f076e63df7b02928b5abf49def827229bb289
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="include-masm"></a>INCLUDE (MASM)
Inserta el código desde el archivo de origen indicado por fuente *filename* en el archivo de origen actual durante el ensamblado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
INCLUDE filename  
```  
  
## <a name="remarks"></a>Comentarios  
 El *filename* deben incluirse entre corchetes angulares si incluye una barra diagonal inversa, punto y coma, mayor-signo, menor-que símbolos, las comillas simples o comillas dobles.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)