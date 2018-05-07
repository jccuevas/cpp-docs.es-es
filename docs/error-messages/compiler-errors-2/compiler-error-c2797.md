---
title: Error del compilador C2797 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2797
dev_langs:
- C++
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea98ab3e6aed4f683fcedad144582e8e946f6d59
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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