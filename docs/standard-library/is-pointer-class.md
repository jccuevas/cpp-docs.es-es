---
title: Clase is_pointer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_pointer
- type_traits/std::is_pointer
dev_langs:
- C++
helpviewer_keywords:
- is_pointer class
- is_pointer
ms.assetid: 44e0a403-7241-4e0a-8922-32877bcb9a4c
caps.latest.revision: 19
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
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: 3bb2597b11ed4b5ebafac0e8548f9ddc18ac5fc4
ms.lasthandoff: 02/24/2017

---
# <a name="ispointer-class"></a>is_pointer (Clase)
Comprueba si el tipo es un puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Ty>  
struct is_pointer;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` es un puntero a `void`, un puntero a un objeto o un puntero a una función, o bien un formulario `cv-qualified` de uno de ellos; en caso contrario, contiene false. Tenga en cuenta que `is_pointer` es false si `Ty` es un puntero a un miembro o a una función miembro.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// std__type_traits__is_pointer.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_pointer<trivial> == " << std::boolalpha   
        << std::is_pointer<trivial>::value << std::endl;   
    std::cout << "is_pointer<int trivial::*> == " << std::boolalpha   
        << std::is_pointer<int trivial::*>::value << std::endl;   
    std::cout << "is_pointer<trivial *> == " << std::boolalpha   
        << std::is_pointer<trivial *>::value << std::endl;   
    std::cout << "is_pointer<int> == " << std::boolalpha   
        << std::is_pointer<int>::value << std::endl;   
    std::cout << "is_pointer<int *> == " << std::boolalpha   
        << std::is_pointer<int *>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_pointer<trivial> == false  
is_pointer<int trivial::*> == false  
is_pointer<trivial *> == true  
is_pointer<int> == false  
is_pointer<int *> == true  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)   
 [Clase is_member_pointer](../standard-library/is-member-pointer-class.md)   
 [Clase is_reference](../standard-library/is-reference-class.md)

