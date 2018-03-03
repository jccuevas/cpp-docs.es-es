---
title: Error del compilador C3489 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3489
dev_langs:
- C++
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4a0115bbb6d00a4e83d0ae3343b1af1b8024002
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3489"></a>Error del compilador C3489
Se necesita 'var' cuando el modo de captura predeterminado es por valor.  
  
 Cuando se especifica que el modo de captura predeterminado de una expresión lambda es por valor, no se puede pasar una variable por valor a la cláusula de captura de dicha expresión.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   No pase explícitamente la variable a la cláusula de captura.  
  
-   No especifique por valor como el modo de captura predeterminado.  
  
-   Especifique por referencia como el modo de captura predeterminado.  
  
-   Pase la variable por referencia a la cláusula de captura. (Esto podría cambiar el comportamiento de la expresión lambda).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3489 porque la variable `n` por valor aparece en la cláusula de captura de una expresión lambda cuyo modo predeterminado es por valor:  
  
```  
// C3489a.cpp  
  
int main()  
{  
   int n = 5;  
   [=, n]() { return n; } (); // C3489  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestran cuatro posibles soluciones para C3489:  
  
```  
// C3489b.cpp  
  
int main()  
{  
   int n = 5;  
  
   // Possible resolution 1:  
   // Do not explicitly pass n to the capture clause.  
   [=]() { return n; } ();  
  
   // Possible resolution 2:  
   // Do not specify by-value as the default capture mode.  
   [n]() { return n; } ();  
  
   // Possible resolution 3:  
   // Specify by-reference as the default capture mode.  
   [&, n]() { return n; } ();  
  
   // Possible resolution 4:  
   // Pass n by reference to the capture clause.  
   [&n]() { return n; } ();  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)