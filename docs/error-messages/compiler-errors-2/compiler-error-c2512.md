---
title: Error del compilador C2512 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2512
dev_langs: C++
helpviewer_keywords: C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63090bc7dac08aa87bcd68e77c076185176a7285
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2512"></a>Error del compilador C2512
'identifier': no hay disponible un constructor predeterminado adecuado  
  
 No hay ningún constructor predeterminado disponible para la clase, estructura o unión especificada. El compilador proporciona un constructor predeterminado solo si no se han proporcionado constructores definidos por el usuario.  
  
 Si usted proporciona un constructor que tome un parámetro distinto de void y desea permitir que la clase se cree sin parámetros, por ejemplo, como los elementos de una matriz, también debe proporcionar un constructor predeterminado. El constructor predeterminado puede ser un constructor con valores predeterminados para todos los parámetros.  
  
 El siguiente ejemplo genera el error C2512 y muestra cómo corregirlo:  
  
```  
// C2512.cpp  
// C2512 expected  
struct B {  
   B (char *);  
   // Uncomment the following line to fix.  
   // B() {};  
};  
  
int main() {  
   B b;   
}  
```  
  
 El siguiente ejemplo muestra un error C2512 más sutil. Para corregir este error, reorganice el código de modo que se defina la clase antes de que se haga referencia a su constructor:  
  
```  
// C2512b.cpp  
// compile with: /c  
struct S {  
   struct X;  
  
   void f() {  
      X *x = new X();   // C2512 X not defined yet  
   }  
  
};  
  
struct S::X {};  
  
struct T {  
   struct X;  
   void f();  
};  
  
struct T::X {};  
  
void T::f() {  
   X *x = new X();  
}  
```  
  
 El error C2512 también puede deberse a una llamada a construir de forma predeterminada una clase que contenga un miembro de datos de referencia o de constante. Estos miembros deben inicializarse en una lista de inicializadores de constructor, que impide que el compilador genere un constructor predeterminado.  
  
 El siguiente ejemplo genera el error C2512 y muestra cómo corregirlo:  
  
```  
// C2512c.cpp  
// Compile by using: cl /c /W3 C2512c.cpp  
struct S {  
   const int i_;  
   int &r_;   
};   
  
int SumS() {  
   const int ci = 7;  
   int ir = 42;  
  
   S s1; // C2512 - no default constructor available  
   S s2{ci, ir};  // Fix - initialize const and reference members   
   return s2.i_ + s2.r_;  
}  
```