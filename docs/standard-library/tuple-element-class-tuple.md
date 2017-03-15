---
title: tuple_element (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tuple_element
- std::tuple_element
- utility/std::tuple_element
dev_langs:
- C++
helpviewer_keywords:
- tuple_element Class
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 54bfdd8a1f095478282af39354a6e9a91ba32891
ms.lasthandoff: 02/24/2017

---
# <a name="tupleelement-class"></a>tuple_element (Clase)
Contiene un elemento `tuple` . Las especializaciones contienen elementos `array` y elementos `pair`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
// CLASS tuple_element (find element by index)  
template <size_t Index, class Tuple>  
   struct tuple_element;  
 
// tuple_element for const 
template <size_t Index, class Tuple>  
   struct tuple_element<Index, const Tuple>;  
 
// tuple_element for volatile  
template <size_t Index, class Tuple>  
   struct tuple_element<Index, volatile Tuple>;  
 
// tuple_element for const volatile  
template <size_t Index, class Tuple>  
   struct tuple_element<Index, const volatile Tuple>;  
 
// Helper typedef
template <size_t Index, class Tuple>  
   using tuple_element_t = typename tuple_element<Index, Tuple>::type; 

// Specialization for arrays  
template <size_t Index, class Elem, size_t Size>  
   struct tuple_element<Index, array<Elem, Size>>;  
  
// Specializations for pairs
// struct to determine type of element 0 in pair
template <class T1, class T2>
   struct tuple_element<0, pair<T1, T2>>;

// struct to determine type of element 1 in pair
template <class T1, class T2>
   struct tuple_element<1, pair<T1, T2>>;
```  
  
### <a name="parameters"></a>Parámetros  
*Índice*  
Índice del elemento designado.  
  
*Tuple*  
El tipo de tupla.  
  
*Elem*  
El tipo de un elemento de matriz.  
  
*Size*  
Se refiere al tamaño de la matriz.  

*T1* El tipo del primer elemento de un par.
  
*T2*  
El tipo del segundo elemento de un par.

## <a name="remarks"></a>Comentarios  
La clase de plantilla `tuple_element` tiene una definición de tipo anidada `type` que es un sinónimo del tipo en el índice `Index` del tipo de tupla `Tuple`.  

La definición de tipo `tuple_element_t` es un alias adecuado para `tuple_element<Index, Tuple>::type`.  
  
La especialización de la clase de plantilla para matrices proporciona una interfaz a un `array` como una tupla de elementos `Size`, cada uno con el mismo tipo. Cada especialización tiene una definición de tipo anidada `type` que es un sinónimo del tipo de elemento `Index` de la `array`, con las calificaciones const o volatile conservadas.  
  
Las especializaciones de plantilla para tipos `pair` tienen una definición de tipo de miembro único, `type`, que es un sinónimo del tipo del elemento en la posición especificada en el par, con cualquier calificador const o volatile conservado. La definición de tipo `tuple_element_t` es un alias adecuado para `tuple_element<N, pair<T1, T2>>::type`.  
  
Use la [función get de &lt;utility&gt;](../standard-library/utility-functions.md#get) para devolver el elemento en una posición especificada o (en C++14 / Visual Studio 2015) de un tipo especificado. 
  
## <a name="example"></a>Ejemplo  
  
```cpp  
#include <tuple>  
#include <string>  
#include <iostream>  
  
using namespace std;  
typedef tuple<int, double, string> MyTuple;  
  
int main() {  
    MyTuple c0{ 0, 1.5, "Tail" };  
  
    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index  
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);  
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type  
  
    cout << val << " " << val2 << " " << val3 << endl;  
}  
```  
  
```Output  
0 1.5 Tail  
```  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
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
```  
  
```Output  
 0 1 2 3  
 0  
```  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
#include <utility>   
#include <iostream>   
  
using namespace std;  
  
typedef pair<int, double> MyPair;  
int main() {  
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
```  
  
```Output  
 0 1.333  
 0 1.333  
```  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<tuple>  
 **Encabezado:** \<array> (para la especialización de matrices)  **Encabezado:** \<utility> (para especializaciones de pares)  **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
[tuple ](../standard-library/tuple-class.md)

