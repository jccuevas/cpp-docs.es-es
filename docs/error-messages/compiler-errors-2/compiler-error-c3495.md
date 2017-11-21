---
title: Error del compilador C3495 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3495
dev_langs: C++
helpviewer_keywords: C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8cf93a5de639ce0c8270ef374eabdedb6c6551bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3495"></a>Error del compilador C3495
'var': una captura lambda debe tener una duración de almacenamiento automática  
  
 No se puede capturar una variable que no tiene una duración de almacenamiento automática, como una variable que está marcada como `static` o `extern`.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   No pase una variable `static` o `extern` a la lista de captura de la expresión lambda.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C3495 porque la variable de `static` `n` aparece en la lista de captura de una expresión lambda:  
  
```  
// C3495.cpp  
  
int main()  
{  
   static int n = 66;  
   [&n]() { return n; }(); // C3495  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)   


