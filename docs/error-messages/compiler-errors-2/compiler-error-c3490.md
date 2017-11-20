---
title: Error del compilador C3490 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3490
dev_langs: C++
helpviewer_keywords: C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 42923edc2d238e7f0b64858561f7d23d211abd80
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3490"></a>Error del compilador C3490
'var' no se puede modificar porque se está accediendo a través de un objeto const.  
  
 Una expresión lambda que se declara en un método `const` no puede modificar los datos de miembro no mutable.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Elimine el modificador `const` de la declaración del método.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3490 porque modifica la variable miembro `_i` en un método `const` :  
  
```  
// C3490a.cpp  
// compile with: /c  
  
class C  
{  
   void f() const   
   {  
      auto x = [=]() { _i = 20; }; // C3490  
   }  
  
   int _i;  
};  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se resuelve C3490 quitando el modificador `const` de la declaración del método:  
  
```  
// C3490b.cpp  
// compile with: /c  
  
class C  
{  
   void f()  
   {  
      auto x = [=]() { _i = 20; };  
   }  
  
   int _i;  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)