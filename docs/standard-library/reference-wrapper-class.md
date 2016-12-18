---
title: "reference_wrapper (Clase) | Microsoft Docs"
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
  - "std.tr1.reference_wrapper"
  - "tr1.reference_wrapper"
  - "reference_wrapper"
  - "tr1::reference_wrapper"
  - "xrefwrap/std::tr1::reference_wrapper"
  - "std::tr1::reference_wrapper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reference_wrapper (clase)"
  - "reference_wrapper (clase) [TR1]"
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
caps.latest.revision: 21
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# reference_wrapper (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Contiene una referencia.  
  
## Sintaxis  
  
```  
template<class Ty>  
    class reference_wrapper  
    : public unary_function<T1, Ret>        // see below  
    : public binary_function<T1, T2, Ret>   // see below  
    {  
public:  
    typedef Ty type;  
    typedef T0 result_type;                 // see below  
  
    reference_wrapper(Ty&);  
  
    Ty& get() const;  
    operator Ty&() const;  
    template<class T1, class T2, ..., class TN>  
        typename result_of<T(T1, T2, ..., TN)>::type  
        operator()(T1&, T2&, ..., TN&);  
  
private:  
    Ty *ptr; // exposition only  
    };  
```  
  
## Comentarios  
 `reference_wrapper<Ty>` es asignable y se puede construir mediante copia, y contiene un puntero que señala a un objeto de tipo `Ty`.  
  
 Una especialización `reference_wrapper<Ty>` se deriva de `std::unary_function<T1, Ret>` \(por lo tanto, define el tipo anidado `result_type` como sinónimo de `Ret` y el tipo anidado `argument_type` como sinónimo de `T1`\) solo si el tipo `Ty` es:  
  
 un tipo de función o un puntero al tipo de función que toma un argumento de tipo `T1` y devuelve `Ret`; o  
  
 un puntero a una función miembro `Ret T::f() cv`, donde `cv` representa los calificadores cv de la función miembro; el tipo `T1` es `cv` `T*`; o  
  
 un tipo de clase que se deriva de `unary_function<T1, Ret>`.  
  
 Una especialización `reference_wrapper<Ty>` se deriva de `std::binary_function<T1, T2, Ret>` \(por lo tanto, define el tipo anidado `result_type` como sinónimo de `Ret`, el tipo anidado `first_argument_type` como sinónimo de `T1` y el tipo anidado `second_argument_type` como sinónimo de `T2`\) solo si el tipo `Ty` es:  
  
 un tipo de función o un puntero al tipo de función que toma dos argumentos de tipo `T1` y `T2` y devuelve `Ret`; o  
  
 un puntero a una función miembro `Ret T::f(T2) cv`, donde `cv` representa los calificadores cv de la función miembro; el tipo `T1` es `cv` `T*`; o  
  
 un tipo de clase que se deriva de `binary_function<T1, T2, Ret>`.  
  
### Constructores  
  
|||  
|-|-|  
|[reference\_wrapper::reference\_wrapper](../Topic/reference_wrapper::reference_wrapper.md)|Construye un objeto `reference_wrapper`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[reference\_wrapper::result\_type](../Topic/reference_wrapper::result_type.md)|Tipo de resultado débil de la referencia ajustada.|  
|[reference\_wrapper::type](../Topic/reference_wrapper::type.md)|Tipo de la referencia ajustada.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[reference\_wrapper::get](../Topic/reference_wrapper::get.md)|Obtiene la referencia ajustada.|  
  
### Operadores  
  
|||  
|-|-|  
|[reference\_wrapper::operator Ty&](../Topic/reference_wrapper::operator%20Ty&.md)|Obtiene un puntero a la referencia ajustada.|  
|[reference\_wrapper::operator\(\)](../Topic/reference_wrapper::operator\(\).md)|Llama a la referencia ajustada.|  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [cref \(Función\)](../Topic/cref%20Function.md)   
 [ref \(Función\)](../Topic/ref%20Function.md)