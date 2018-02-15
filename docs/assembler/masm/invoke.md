---
title: INVOKE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Invoke
dev_langs:
- C++
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4876fa0a6e63addf529e7c458e052aff77ebc6a1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="invoke"></a>INVOKE
Llama al procedimiento en la dirección proporcionada por *expresión*, pasando los argumentos en la pila o en los registros según las convenciones de llamada estándares del tipo de lenguaje.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
INVOKE   
expression [[, arguments]]  
```  
  
## <a name="remarks"></a>Comentarios  
 Cada argumento pasado al procedimiento puede ser una expresión, un par de registros o una expresión de dirección (precedida de una expresión `ADDR`).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)