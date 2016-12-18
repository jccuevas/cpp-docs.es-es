---
title: "is_pod (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.is_pod"
  - "is_pod"
  - "std::tr1::is_pod"
  - "std.is_pod"
  - "std::is_pod"
  - "type_traits/std::is_pod"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_pod (clase) [TR1]"
  - "is_pod"
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_pod (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es POD.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_pod;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 `is_pod<Ty>::value` es `true` si el tipo `Ty` es datos antiguos sin formato \(POD\).  De lo contrario, es `false`.  
  
 Los tipos aritméticos, tipos de enumeración, tipos de puntero y el puntero a tipos de miembro son POD.  
  
 Una versión cv completa de un tipo POD es en sí misma un tipo POD.  
  
 Una matriz de POD es en sí misma POD.  
  
 Una estructura o unión cuyos miembros de datos no estáticos son todos POD, es en sí misma POD si reúne estas condiciones:  
  
-   No hay ningún constructor declarado por el usuario.  
  
-   No hay ningún miembro de datos no estáticos privado o protegido.  
  
-   Ninguna clase base.  
  
-   No hay funciones virtuales.  
  
-   No hay ningún miembro de datos no estáticos de tipo de referencia.  
  
-   No hay ningún operador de asignación de copia definido por el usuario.  
  
-   No hay ningún destructor definido por el usuario.  
  
 Por lo tanto, puede compilar recursivamente estructuras y matrices POD que contienen estructuras y matrices POD.  
  
## Ejemplo  
  
```  
// std_tr1__type_traits__is_pod.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct throws   
    {   
    throws() throw(int)   
        {   
        }   
  
    throws(const throws&) throw(int)   
        {   
        }   
  
    throws& operator=(const throws&) throw(int)   
        {   
        }   
  
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_pod<trivial> == " << std::boolalpha   
        << std::is_pod<trivial>::value << std::endl;   
    std::cout << "is_pod<int> == " << std::boolalpha   
        << std::is_pod<int>::value << std::endl;   
    std::cout << "is_pod<throws> == " << std::boolalpha   
        << std::is_pod<throws>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_pod\<trivial\> \=\= true**  
**is\_pod\<int\> \=\= true**  
**is\_pod\<throws\> \=\= false**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)