---
title: add_rvalue_reference (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::add_rvalue_reference
dev_langs: C++
helpviewer_keywords: add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 605e428c0712a657b7b3d0df35558a61c6dbc54a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference (clase)
Si es un tipo de objeto o función, crea un tipo de referencia a un valor R del parámetro de plantilla. De lo contrario, debido a la semántica de contracción de referencias, el tipo es el mismo que el parámetro de plantilla.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```  
  
#### <a name="parameters"></a>Parámetros  
 T  
 Tipo que se va a modificar.  
  
## <a name="remarks"></a>Comentarios  
 La clase `add_rvalue_reference` tiene un miembro denominado `type` que es un alias del tipo de una referencia a un valor R al parámetro de plantilla `T`. La semántica de contracción de referencias implica que, en los tipos `T` que no son de objeto ni de función, `T&&` sea `T`. Por ejemplo, cuando `T` es un tipo de referencia a un valor L, `add_rvalue_reference<T>::type` es el tipo de referencia a un valor L, no una referencia a un valor R.  
  
 Por comodidad, <type_traits> define una plantilla auxiliar, `add_rvalue_reference_t`, que es el alias del `type` miembro de `add_rvalue_reference`.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo de código se usa static_assert para mostrar cómo se crean tipos de referencia a un valor R mediante `add_rvalue_reference` y `add_rvalue_reference_t` y cómo el resultado de `add_rvalue_reference` en un tipo de referencia a un valor R no es una referencia a un valor R, sino que se contrae en el tipo de referencia a un valor L.  
  
```cpp  
// ex_add_rvalue_reference.cpp  
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp  
#include <type_traits>   
#include <iostream>   
#include <string>  
  
using namespace std;  
int main()  
{  
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,   
        "Expected add_rvalue_reference_t<string> to be string&&");  
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,   
        "Expected add_rvalue_reference_t<string*> to be string*&&");  
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,   
        "Expected add_rvalue_reference_t<string&> to be string&");  
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,   
        "Expected add_rvalue_reference_t<string&&> to be string&&");  
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;  
    return 0;  
}  
  
/*Output:  
All static_assert tests of add_rvalue_reference passed.  
*/  
```  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: <type_traits> Espacio de nombres: std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)   
 [Clase add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)   
 [is_rvalue_reference (Clase)](../standard-library/is-rvalue-reference-class.md)
