---
title: "tuple_element (clase) &lt;tuple&gt; | Microsoft Docs"
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
  - "tuple_element (clase) <tuple> (TR1)"
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple_element (clase) &lt;tuple&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ajusta un `tuple` elemento.  
  
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
 
template <size_t Index, class Tuple>  
using tuple_element_t = typename tuple_element<Index, Tuple>::type;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Index`  
 Índice del elemento designado.  
  
 `Tuple`  
 El tipo de tupla.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla tiene una definición de tipo anidado `type` que es un sinónimo para el tipo en el índice `Index` del tipo de tupla `Tuple`.  
  
## <a name="example"></a>Ejemplo  
  
```  
#include <tuple>  
#include <string>  
#include <iostream>  
  
using namespace std;  
typedef tuple<int, double, string> MyTuple;  
  
int main()  
{  
  
    MyTuple c0{ 0, 1.5, "Tail" };  
  
    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index  
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);  
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type  
  
    cout << val << " " << val2 << " " << val3 << endl;  
}  
  
/*  
Output:  
0 1.5 Tail  
*/  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< tupla>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
[tupla ](../standard-library/tuple-class.md)
    
 [tuple_element)](../standard-library/tuple-element-class-tuple.md)
