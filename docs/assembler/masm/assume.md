---
title: SUPONGA | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ASSUME
dev_langs: C++
helpviewer_keywords: ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6046d19e628e75dee6e3f33b400c48dcbf317735
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="assume"></a>ASSUME
Habilita la comprobación de valores de registro de errores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ASSUME segregister:name [[, segregister:name]]...  
ASSUME dataregister:type [[, dataregister:type]]...  
ASSUME register:ERROR [[, register:ERROR]]...  
ASSUME [[register:]] NOTHING [[, register:NOTHING]]...  
```  
  
## <a name="remarks"></a>Comentarios  
 Después de un `ASSUME` se coloca en efecto, el ensamblador inspecciona los cambios a los valores de los registros determinados. **ERROR** genera un error si se usa el registro. **NADA** quita registra la comprobación de errores. Puede combinar diferentes tipos de supuestos en una sola instrucción.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)