---
title: __restrict | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __restrict
- __restrict_cpp
dev_langs:
- C++
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: c0ed875845323d4125a97ca004bb50385f59c53d
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="restrict"></a>__restrict
Al igual que el **__declspec ( [restringir](../cpp/restrict.md) )** modificador, el `__restrict` palabra clave indica que un símbolo no es un alias en el ámbito actual. La palabra clave `__restrict` difiere del modificador `__declspec ( restrict )` en lo siguiente:  
  
-   La palabra clave `__restrict` solo es válida en variables y `__declspec ( restrict )` solo es válido en declaraciones de función y definiciones.  
  
-   `__restrict` es similar a `restrict` de la especificación C99, pero `__restrict` se puede utilizar en programas de C++ o C.  
  
-   Cuando se utiliza `__restrict`, el compilador no propagará la propiedad sin alias de una variable. Es decir, si se asigna una variable `__restrict` a una variable que no es `__restrict`, el compilador seguirá permitiendo que la variable que no es __restrict tenga un alias. Este comportamiento es diferente del de la palabra clave `restrict` de la especificación C99.  
  
 Normalmente, si se modifica el comportamiento de una función completa, es mejor usar `__declspec ( restrict )` que la palabra clave.  
  
 En Visual Studio de 2015 y versiones posteriores, se puede usar `__restrict` en las referencias de C++.  
  
> [!NOTE]
>  Cuando se utiliza en una variable que tiene también la [volátiles](../cpp/volatile-cpp.md) palabra clave, `volatile` tendrá prioridad.  
  
## <a name="example"></a>Ejemplo  
  
```  
// __restrict_keyword.c  
// compile with: /LD  
// In the following function, declare a and b as disjoint arrays  
// but do not have same assurance for c and d.  
void sum2(int n, int * __restrict a, int * __restrict b,   
          int * c, int * d) {  
   int i;  
   for (i = 0; i < n; i++) {  
      a[i] = b[i] + c[i];  
      c[i] = b[i] + d[i];  
    }  
}  
  
// By marking union members as __restrict, tell compiler that  
// only z.x or z.y will be accessed in any given scope.  
union z {  
   int * __restrict x;  
   double * __restrict y;  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)
