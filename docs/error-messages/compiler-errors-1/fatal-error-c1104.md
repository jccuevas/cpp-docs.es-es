---
title: Error irrecuperable C1104 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1104
dev_langs:
- C++
helpviewer_keywords:
- C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 7a3f7fbff36f998716bc6639ccb718b1699ccf80
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1104"></a>Error irrecuperable C1104
error irrecuperable al importar el libid: 'mensaje'  
  
 El compilador detectó un problema al importar una biblioteca de tipos.  Por ejemplo, no puede especificar una biblioteca de tipos con libid y especificar `no_registry`también.  
  
 Para obtener más información, consulte [#import (directiva)](../../preprocessor/hash-import-directive-cpp.md).  
  
 El ejemplo siguiente generará el error C1104:  
  
```  
// C1104.cpp  
#import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104  
```
