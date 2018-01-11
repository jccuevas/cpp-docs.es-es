---
title: tuple_size (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
dev_langs: C++
helpviewer_keywords: std::tuple_size
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ef3d1fae353de8962684b080c223bd4a6a235acf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tuplesize-class"></a>tuple_size (Clase);
Informa el número de elementos que contiene una `tuple` .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
// TEMPLATE STRUCT tuple_size  
template <class Tuple>  
   struct tuple_size;  
  
// number of elements in array  
template <class Elem, size_t Size>  
   struct tuple_size<array<Elem, Size>>  
      : integral_constant<size_t, Size>; 
  
// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>> 
      : integral_constant<size_t, 2>

// size of tuple  
template <class... Types>  
   struct tuple_size<tuple<Types...>>  
      : integral_constant<size_t, sizeof...(Types)>;  
  
// size of const tuple  
template <class Tuple>  
   struct tuple_size<const Tuple>;  
  
// size of volatile tuple  
template <class Tuple>  
   struct tuple_size<volatile Tuple>;  
  
// size of const volatile tuple  
template <class Tuple>  
   struct tuple_size<const volatile Tuple>;   
```  
  
#### <a name="parameters"></a>Parámetros  
*Tuple*  
El tipo de tupla. 
  
*Elem*  
El tipo de los elementos de la matriz. 
  
*Size*  
Se refiere al tamaño de la matriz. 
  
*T1*  
El tipo del primer miembro del par. 
  
*T2*  
El tipo del segundo miembro del par. 
  
*Tipos*  
Los tipos de los elementos de tupla. 
  
  
## <a name="remarks"></a>Comentarios  
La clase de plantilla tiene un miembro `value` que es una expresión constante entera cuyo valor es la extensión del tipo de tupla `Tuple`.  
  
La especialización de plantilla para matrices tiene un miembro `value` que es una expresión constante entera cuyo valor es `Size`, que es el tamaño de la matriz.  
  
La especialización de plantilla para pares tiene un miembro `value` que es una expresión constante entera cuyo valor es 2.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
#include <tuple>   
#include <iostream>  
  
using namespace std;  
  
typedef tuple<int, double, int, double> MyTuple;  
int main()  
{  
    MyTuple c0(0, 1.5, 2, 3.7);  
  
    // display contents " 0 1 2 3"   
    cout << " " << get<0>(c0);  
    cout << " " << get<1>(c0);  
    cout << " " << get<2>(c0);  
    cout << " " << get<3>(c0) << endl;  
  
    // display size " 4"   
    cout << " " << tuple_size<MyTuple>::value << endl;  
}  
```  
  
```Output  
 0 1.5 2 3.7  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<tuple>  
 **Encabezado:** \<array> (para la especialización de matrices)  
 **Encabezado:** \<utility> (para la especialización de pares)  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [\<tuple>](../standard-library/tuple.md)   
 [tuple](../standard-library/tuple-class.md)  
 [tuple_element (Clase)](../standard-library/tuple-element-class-tuple.md)
