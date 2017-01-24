---
title: "tuple_size (clase) &lt;array&gt; | Microsoft Docs"
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
  - "tuple_size"
  - "std::tr1::tuple_size"
  - "std.tr1.tuple_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tuple_size (clase) <array> (TR1)"
ms.assetid: ef95ffee-59b4-4396-817f-487d4486772d
caps.latest.revision: 20
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple_size (clase) &lt;array&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ajusta el tamaño de una matriz.  
  
## Sintaxis  
  
```  
template<class Tuple>  
struct tuple_size;  
  
// struct to determine number of elements in array  
template<class T, size_t Size>  
struct tuple_size<array<T, Size> >  
: integral_constant<size_t, Size>;  
  
// size of const tuple  
template<class Tuple>  
struct tuple_size<const Tuple>;  
  
// size of volatile tuple  
template<class Tuple>  
struct tuple_size<volatile Tuple>;  
  
// size of const volatile tuple  
template<class Tuple>  
struct tuple_size<const volatile Tuple>;  
  
```  
  
## Parámetros de plantilla  
 `T`  
 El tipo de un elemento.  
  
 `Size`  
 Se refiere al tamaño de la matriz.  
  
## Comentarios  
 Esta plantilla es una especialización de la clase de plantilla [tuple\_size \(Clase\)](../standard-library/tuple-size-class-tuple.md). Tiene un miembro `value` que es una expresión constante entera cuyo valor es `N`, que es el tamaño de la matriz.  
  
## Ejemplo  
  
```  
#include <array>   
#include <iostream>   
  
using namespace std;  
  
typedef array<int, 4> MyArray;  
  
int main()  
{  
    MyArray c0 { 0, 1, 2, 3 };  
  
    // display contents " 0 1 2 3"   
    for (const auto& e : c0)  
    {  
        cout << e;  
    }  
    cout << endl;  
  
    // display size " 4"   
    cout << " " << tuple_size<MyArray>::value << endl;  
}  
/*  
Output:  
0123  
4  
*/  
  
```  
  
## Requisitos  
 **Encabezado:** \<array\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<array\>](../standard-library/array.md)   
 [\<tuple\>](../standard-library/tuple.md)   
 [tuple\_size \(Clase\)](../standard-library/tuple-size-class-tuple.md)