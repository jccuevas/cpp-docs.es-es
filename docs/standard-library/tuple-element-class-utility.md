---
title: "tuple_element (clase) &lt;utility&gt; | Microsoft Docs"
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
  - "tuple_element (clase) <utility> (TR1)"
ms.assetid: f9db79e8-685c-49e3-97ee-81763e516ce3
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple_element (clase) &lt;utility&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ajusta el tipo de un elemento `pair`.  
  
## Sintaxis  
  
```  
// CLASS tuple_element (find element by index)  
template<size_t Index, class Tuple>  
struct tuple_element;  
  
// struct to determine type of element 0 in pair  
template<class Ty1, class Ty2>  
struct tuple_element<0, pair<Ty1, Ty2> >;  
  
// struct to determine type of element 1 in pair  
template<class Ty1, class Ty2>  
struct tuple_element<1, pair<Ty1, Ty2> >;  
  
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
  
#### Parámetros  
 Índice  
 La posición del elemento. Para par, el valor es 0 o 1.  
  
 `T1`  
 El tipo del primer elemento par.  
  
 `T2`  
 El tipo del segundo elemento par.  
  
 tipo  
  
## Comentarios  
 Las plantillas son especializaciones de la clase de plantilla [tuple\_element \(Clase\)](../standard-library/tuple-element-class-tuple.md). Cada una tiene una definición de tipo de miembro único, `type`, que es un sinónimo del tipo del elemento en la posición especificada en el `pair`, con cualquier calificador const o volatile conservado.`tuple_element_t`es un alias adecuado para `tuple_element<N, pair<T1, T2>>::type`. Use la [get \(Función\)](../Topic/get%20Function%20%3Cutility%3E.md) para devolver el elemento en una posición especificada o \(en C\+\+14 \/ Visual Studio 2015\) de un tipo especificado.  
  
## Ejemplo  
  
```  
#include <utility>   
#include <iostream>   
  
using namespace std;  
  
typedef pair<int, double> MyPair;  
int main()  
{  
    MyPair c0(0, 1.333);  
  
    // display contents " 0 1"   
    cout << " " << get<0>(c0);  
    cout << " " << get<1>(c0) << endl;  
  
    // display first element " 0" by index  
    tuple_element<0, MyPair>::type val = get<0>(c0);  
    cout << " " << val;  
  
    // display second element by type   
    tuple_element<1, MyPair>::type val2 = get<double>(c0);  
    cout << " " << val2 << endl;  
}  
  
/*  
Output:  
0 1.333  
0 1.333  
*/  
```  
  
## Requisitos  
 **Encabezado:** \<utility\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<utility\>](../standard-library/utility.md)   
 [get \(Función\)](../Topic/get%20Function%20%3Cutility%3E.md)   
 [tuple\_size \(Clase\)](../standard-library/tuple-size-class-utility.md)