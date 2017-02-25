---
title: "tuple_size (Clase) &lt;tuple&gt;  | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "tuple_size (clase) <tuple> (TR1)"
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# tuple_size (Clase) &lt;tuple&gt; 
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Informa del número de elementos que un `tuple` contiene.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
// TEMPLATE STRUCT tuple_size  
template <class Tuple>  
struct tuple_size;  
 
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
 `Tuple`  
 El tipo de tupla.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla tiene un miembro `value` que es una expresión constante entera cuyo valor es la extensión del tipo de tupla `Tuple`.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
  
/*  
Output:  
0 1.5 2 3.7  
4  
*/  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< tupla>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [\< tupla>](../standard-library/tuple.md)   
 [tupla](../standard-library/tuple-class.md)  
 [tuple_element (clase)](../standard-library/tuple-element-class-tuple.md)
