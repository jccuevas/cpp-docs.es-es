---
title: Error del compilador C2797 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2797
dev_langs:
- C++
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
caps.latest.revision: 5
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 5eea0aae37627015f8723835e4e3e1cb0c6d2e94
ms.lasthandoff: 04/24/2017

---
# <a name="compiler-error-c2797"></a>Error del compilador C2797
(Obsoleto) No se implementa la inicialización de la lista dentro de la lista de inicializadores de miembro o un inicializador de miembro de datos no estáticos.  
  
 Esta advertencia es obsoleta en Visual Studio 2015. En Visual Studio 2013 y versiones anteriores, el compilador de Visual C++ no implementa la inicialización de la lista dentro de una lista de inicializadores de miembro o un inicializador de miembro de datos no estáticos. Antes de Visual Studio 2013 Update 3, esto se convertía de manera automática en una llamada de función, lo que podía hacer que se generase código incorrecto. Visual Studio 2013 Update 3 lo notifica como un error.  
  
 En este ejemplo se genera C2797:  
  
```  
#include <vector>  
struct S {  
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'  
  
    std::vector<int> v1;  
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'  
};  
  
```  
  
 En este ejemplo también se genera C2797:  
  
```  
struct S1 {  
    int i;  
};  
  
struct S2 {  
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664  
    S1 s1;  
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664  
};  
  
```  
  
 Para corregir este problema, puede utilizar la construcción explícita de listas internas. Por ejemplo:  
  
```  
#include <vector>  
typedef std::vector<int> Vector;  
struct S {  
    S() : v1(Vector{1}) {}  
  
    Vector v1;  
    Vector v2 = Vector{1, 2};  
};  
  
```  
  
 Si no se requiere la inicialización de la lista:  
  
```  
struct S {  
    S() : s1("") {}  
  
    std::string s1;  
    std::string s2 = std::string("");  
};  
  
```  
  
 (El compilador de Visual Studio 2013 lo hace implícitamente en versiones anteriores a Visual Studio 2013 Update 3.)
