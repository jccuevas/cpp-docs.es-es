---
title: Error del compilador C2388 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2388
dev_langs:
- C++
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa9f970d71be7b19551ef5029df49b696eb353e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2388"></a>Error del compilador C2388
'símbolo': un símbolo no se puede declarar con ambos __declspec y \__declspec(process)  
  
 Los modificadores `appdomain` y `process` `__declspec` no pueden usarse en el mismo símbolo. El almacenamiento que existe para una variable es por proceso o por dominio de aplicación.  
  
 Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).  
  
 El ejemplo siguiente genera la advertencia C2388:  
  
```  
// C2388.cpp  
// compile with: /clr /c  
__declspec(process) __declspec(appdomain) int i;   // C2388  
__declspec(appdomain) int i;   // OK  
```