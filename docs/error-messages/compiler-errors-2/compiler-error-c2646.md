---
title: Error de compilador Error C2646 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2646
dev_langs:
- C++
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 353f65b4d9702ed82ff92eae63fcedaa6adba227
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2646"></a>Error C2646 de Error del compilador
Una unión o un struct anónimo en un ámbito global o de espacio de nombres se debe declarar como static  
  
 Una unión o un struct anónimo tiene un ámbito global o de espacio de nombres pero no se ha declarado como `static`.  
  
 El ejemplo siguiente genera el error C2646 y muestra cómo corregirlo:  
  
```  
// C2646.cpp  
// compile with: /c  
union { int i; };   // C2646 not static  
  
// OK  
static union { int j; };  
union U { int i; };  
```
