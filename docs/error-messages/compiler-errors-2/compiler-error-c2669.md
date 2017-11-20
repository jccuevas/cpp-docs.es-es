---
title: C2669 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2669
dev_langs: C++
helpviewer_keywords: C2669
ms.assetid: f9cb8111-bcdc-484b-a863-2c42e15a0496
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0cd56be9cba1fcefa269f30579dcace4f3166660
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2669"></a>C2669 de Error del compilador
función miembro no permitida en una unión anónima  
  
[Uniones anónimas](../../cpp/unions.md#anonymous_unions) no puede tener funciones miembro.  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera C2669:  
  
```cpp  
// C2669.cpp  
struct X {  
   union {  
      int i;  
      void f() {   // C2669, remove function  
         i = 0;   
      }  
   };  
};  
```  
  