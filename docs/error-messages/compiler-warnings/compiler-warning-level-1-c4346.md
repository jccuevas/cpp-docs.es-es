---
title: "Advertencia del compilador (nivel 1) C4346 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4346"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4346"
ms.assetid: 68ee562d-cca9-4a2a-9a1b-14ad1a1e7396
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 1) C4346
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre' : un nombre dependiente no es un tipo  
  
 La palabra clave [typename](../../cpp/typename.md) es necesaria si se va a tratar un nombre dependiente como un tipo.  Éste es un cambio importante en el compilador de Visual C\+\+ .NET 2003 implementado para cumplir el estándar ISO C\+\+.  
  
 Para que el código funcione de igual forma en todas las versiones de Visual C\+\+, agregue `typename` a la declaración.  
  
 El código siguiente genera el error C4346:  
  
```  
// C4346.cpp  
// compile with: /WX /LD  
template<class T>  
struct C {  
   T::X* x;   // C4346  
   // try the following line instead  
   // typename T::X* x;  
};  
```  
  
 En los ejemplos siguientes se muestran otros contextos en los que la palabra clave **typename** es necesaria:  
  
```  
// C4346b.cpp  
// compile with: /LD /W1  
template<class T>  
const typename T::X& f(typename T::Z* p);   // Required in both places  
  
template<class T, int N>  
struct L{};  
  
template<class T>  
struct M : public L<typename T::Type, T::Value>   
{   // required on type argument, not on non-type argument  
   typedef typename T::X   Type;  
   Type f();   // OK: "Type" is a type-specifer  
   typename T::X g();   // typename required  
   operator typename T::Z();   // typename required      
};  
```  
  
 y en este otro,  
  
```  
// C4346c.cpp  
// compile with: /LD /WX  
struct Y {  
   typedef int Y_t;  
};  
  
template<class T>  
struct A {  
   typedef Y A_t;  
};  
  
template<class T>  
struct B {  
   typedef /*typename*/ A<T>::A_t B_t;   // C4346 typename needed here  
   typedef /*typename*/ B_t::Y_t  B_t2;   // typename also needed here  
};  
```