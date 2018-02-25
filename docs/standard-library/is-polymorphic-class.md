---
title: Clase is_polymorphic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_polymorphic
dev_langs:
- C++
helpviewer_keywords:
- is_polymorphic class
- is_polymorphic
ms.assetid: 4e1704db-d6f9-4154-a100-0ba02a373f20
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d9633e82e68ea95e276d554cfaf6212e30ba15b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ispolymorphic-class"></a>is_polymorphic (Clase)
Comprueba si el tipo tiene una función virtual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Ty>  
struct is_polymorphic;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que declara o hereda una función virtual; en caso contrario, contiene false.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// std__type_traits__is_polymorphic.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct throws   
    {   
    throws() throw(int)   
        {   
        }   
  
    throws(const throws&) throw(int)   
        {   
        }   
  
    throws& operator=(const throws&) throw(int)   
        {   
        }   
  
    virtual ~throws()   
        {   
        }   
  
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_polymorphic<trivial> == " << std::boolalpha   
        << std::is_polymorphic<trivial>::value << std::endl;   
    std::cout << "is_polymorphic<throws> == " << std::boolalpha   
        << std::is_polymorphic<throws>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_polymorphic<trivial> == false  
is_polymorphic<throws> == true  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)   
 [Clase is_abstract](../standard-library/is-abstract-class.md)
