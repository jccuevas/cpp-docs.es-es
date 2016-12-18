---
title: "tuple_element (clase) &lt;array&gt; | Microsoft Docs"
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
  - "std.tr1.tuple_element"
  - "tuple_element"
  - "std::tr1::tuple_element"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tuple_element (clase) <array> (TR1)"
ms.assetid: 99201ca4-190a-4d9e-9013-de95ddfe5901
caps.latest.revision: 21
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple_element (clase) &lt;array&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Contiene el tipo de un elemento de matriz.  
  
## Sintaxis  
  
```  
// CLASS tuple_element (find element by index)  
template<size_t Index, class Tuple>  
struct tuple_element;  
  
template<size_t Index, class T, size_t Size>  
struct tuple_element<Index, array<T, Size>>  
  
// tuple_element for const  
template<size_t Index, class Tuple>  
struct tuple_element<Index, const Tuple>;  
  
// tuple_element for volatile  
template<size_t Index, class Tuple>  
struct tuple_element<Index, volatile Tuple>;  
  
// tuple_element for const volatile  
template<size_t Index, class Tuple>  
struct tuple_element<Index, const volatile Tuple>;  
  
template<size_t Index, class Tuple>  
using tuple_element_t = typename tuple_element<Index, Tuple>::type;  
  
```  
  
## Parámetros  
 `Index`  
 La posición del elemento.  
  
 `T`  
 El tipo de un elemento.  
  
 `N`  
 Se refiere al tamaño de la matriz.  
  
## Comentarios  
 Esta clase de plantilla es una especialización de la clase de plantilla [tuple\_element \(Clase\)](../standard-library/tuple-element-class-tuple.md) para matrices. La clase proporciona una interrelación a una matriz como una tupla de N elementos, cada uno de los cuales tiene el mismo tipo. Cada especialización tiene una definición de tipo anidada `type` que es un sinónimo del tipo de elemento `Index` de la `array`, con las calificaciones const o volatile conservadas.  
  
## Ejemplo  
  
```  
  
#include <array>   
#include <iostream>   
  
using namespace std;  
typedef array<int, 4> MyArray;  
  
int main()  
{  
    MyArray c0 { 0, 1, 2, 3 };  
  
    for (const auto& e : c0)  
    {  
        cout << " " << e;  
    }  
    cout << endl;  
  
    // display first element " 0"   
    tuple_element<0, MyArray>::type val = c0.front();  
    cout << " " << val << endl;  
}  
  
/*  
Output:  
0 1 2 3  
0  
*/  
  
```  
  
## Requisitos  
 **Encabezado:** \<array\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<array\>](../standard-library/array.md)   
 [\<tuple\>](../standard-library/tuple.md)   
 [tuple\_element \(Clase\)](../standard-library/tuple-element-class-tuple.md)