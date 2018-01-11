---
title: Error del compilador C2248 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2248
dev_langs: C++
helpviewer_keywords: C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5493e6e91a639b83adcddcbd1f680d29ce9f9dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2248"></a>Error del compilador C2248
'*miembro*': no se puede obtener acceso a '*access_level*'miembro declarado en la clase'*clase*'  
  
No se pueden obtener acceso los miembros de una clase derivada `private` los miembros de una clase base. No se puede tener acceso a `private` o `protected` los miembros de instancias de clase.  
  
## <a name="example"></a>Ejemplo  
  
El ejemplo siguiente genera C2248 cuando privado o protegidos miembros de una clase se obtiene acceso desde fuera de la clase. Para corregir este problema, no tener acceso a estos miembros directamente fuera de la clase. Usar funciones de miembro y datos de miembro público para interactuar con la clase.  
  
```cpp  
// C2248_access.cpp 
// compile with: cl /EHsc /W4 C2248_access.cpp 
#include <stdio.h>  

class X {  
public:  
    int  m_publicMember;  
    void setPrivateMember( int i ) {  
        m_privateMember = i;  
        printf_s("\n%d", m_privateMember);  
    }  
protected:  
    int  m_protectedMember;  
  
private:  
    int  m_privateMember;  
} x;  
  
int main() {  
    x.m_publicMember = 4;  
    printf_s("\n%d", x.m_publicMember);  
    x.m_protectedMember = 2; // C2248 m_protectedMember is protected  
    x.m_privateMember = 3;   // C2248  m_privMemb is private  
    x.setPrivateMember(0);   // OK uses public access function  
}  
```  
  
Otro problema de ajuste que expone C2248 es el uso de especialización y friends de plantilla. Para corregir este problema, declare friend funciones de plantilla mediante un <> de lista de parámetros de plantilla vacía o parámetros de plantilla específica.  
  
```cpp  
// C2248_template.cpp 
// compile with: cl /EHsc /W4 C2248_template.cpp 
template<class T>  
void f(T t) {  
    t.i;   // C2248  
}  
  
struct S {  
private:  
    int i;  
  
public:  
    S() {}  
    friend void f(S);   // refer to the non-template function void f(S)  
    // To fix, comment out the previous line and
    // uncomment the following line.  
    // friend void f<S>(S);  
};  
  
int main() {  
    S s;  
    f<S>(s);  
}  
```  
  
Otro problema de ajuste que expone C2248 es cuando se intenta declarar a un elemento friend de una clase y cuando la clase no es visible para la declaración friend en el ámbito de la clase. Para corregir este problema, conceda confianza a la clase envolvente.  
  
```cpp  
// C2248_enclose.cpp  
// compile with: cl /W4 /c C2248_enclose.cpp  
class T {  
    class S {  
        class E {};  
    };  
    friend class S::E;   // C2248  
};  
  
class A {  
    class S {  
        class E {};  
        friend class A;  // grant friendship to enclosing class  
    };  
    friend class S::E;   // OK  
};  
```