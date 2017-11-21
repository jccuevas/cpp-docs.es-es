---
title: Compilador advertencia (nivel 1) C4286 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4286
dev_langs: C++
helpviewer_keywords: C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 71abc86a66f08cbdceb422b74fa5ca600b110a0f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4286"></a>Advertencia del compilador (nivel 1) C4286
'type1': ha sido detectado por la clase base ('tipo2') en la línea número  
  
 El tipo de excepción especificada está controlado por un controlador anterior. El tipo del segundo elemento catch se deriva el tipo de la primera. Excepciones para una clase base detectar excepciones para una clase derivada.  
  
## <a name="example"></a>Ejemplo  
  
```  
//C4286.cpp  
// compile with: /W1  
#include <eh.h>  
class C {};  
class D : public  C {};  
int main()  
{  
    try  
    {  
        throw "ooops!";  
    }  
    catch( C ) {}  
    catch( D ) {}  // warning C4286, D is derived from C  
}  
```