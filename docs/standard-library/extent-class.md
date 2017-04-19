---
title: extent (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- extent
- type_traits/std::extent
dev_langs:
- C++
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
caps.latest.revision: 20
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 23cf8230cd5b8adb7975ec21a249d9efc4d66c71
ms.lasthandoff: 02/24/2017

---
# <a name="extent-class"></a>extent (Clase)
Obtiene una dimensión de matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Ty, unsigned I = 0>  
struct extent;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
 `I`  
 La matriz que se enlaza a la consulta.  
  
## <a name="remarks"></a>Comentarios  
 Si `Ty` es un tipo de matriz con `I` dimensiones como mínimo, la consulta de tipo contiene el número de elementos de la dimensión que especifica `I`. Si `Ty` no es un tipo de matriz o el rango es menor que `I`, o si `I` es cero y `Ty` es de tipo "matriz de límite desconocido de `U`", la consulta de tipo contiene el valor 0.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// std__type_traits__extent.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "extent 0 == "   
        << std::extent<int[5][10]>::value << std::endl;   
    std::cout << "extent 1 == "   
        << std::extent<int[5][10], 1>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
extent 0 == 5  
extent 1 == 10  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)   
 [remove_all_extents (Clase)](../standard-library/remove-all-extents-class.md)   
 [remove_extent (Clase)](../standard-library/remove-extent-class.md)

