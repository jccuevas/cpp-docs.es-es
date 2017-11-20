---
title: _CIlog | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIlog
apilocation:
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _CIlog
- CIlog
dev_langs: C++
helpviewer_keywords:
- _CIlog intrinsic
- CIlog intrinsic
ms.assetid: 23503854-ddaa-4fe0-a4a3-7fbb3a43bdec
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1ba78f83dd288d03ab08fc1ce11fc8b219371704
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cilog"></a>_CIlog
Calcula el logaritmo natural del valor superior de la pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __cdecl _CIlog();  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta versión de la función `log` tiene una convención de llamada especializada que el compilador entiende. Acelera la ejecución porque evita que se generen copias y ayuda con la asignación de registros.  
  
 El valor resultante se inserta en la parte superior de la pila.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** x86  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log, logf, log10, log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)