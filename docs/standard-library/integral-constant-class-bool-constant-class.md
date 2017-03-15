---
title: integral_constant (Clase), bool_constant (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- integral_constant
- std::integral_constant
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- bool_constant
- std::bool_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
dev_langs:
- C++
helpviewer_keywords:
- integral_constant class
- integral_constant
- bool_constant
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
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
ms.sourcegitcommit: 8630a5c0b97b85e0dc75e8b470974bb7d223a511
ms.openlocfilehash: 6c71c3571e19c57b13c827bbb84e347e3ff26b01
ms.lasthandoff: 02/24/2017

---
# <a name="integralconstant-class-boolconstant-class"></a>Clase integral_constant, clase bool_constant
Crea una constante entera a partir de un tipo y un valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T, T v>
struct integral_constant {  
   static constexpr T value = v;  
   typedef T value_type;  
   typedef integral_constant<T, v> type;  
   constexpr operator value_type() const noexcept;  
   constexpr value_type operator()() const noexcept;  
   };  
```
  
### <a name="parameters"></a>Parámetros  
*T*  
Tipo de la constante.  
  
*v*  
Valor de la constante.  
  
## <a name="remarks"></a>Comentarios  
La clase de plantilla `integral_constant`, si está especializada con un tipo entero *T* y un valor *v* de ese tipo, representa un objeto que contiene una constante de ese tipo entero con el valor especificado. El miembro denominado `type` es un alias para el tipo de especialización de la plantilla generada y el miembro `value` contiene el valor *v* usado para crear la especialización.  
  
La clase de plantilla `bool_constant` es una especialización parcial explícita de `integral_constant` que usa `bool` como argumento *T*.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// std__type_traits__integral_constant.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "integral_constant<int, 5> == "   
        << std::integral_constant<int, 5>::value << std::endl;   
    std::cout << "integral_constant<bool, false> == " << std::boolalpha   
        << std::integral_constant<bool, false>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
integral_constant<int, 5> == 5  
integral_constant<bool, false> == false  
```  
  
## <a name="requirements"></a>Requisitos  

**Encabezado:** \<type_traits>
  
**Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)   
 [Definición de tipo false_type](../standard-library/type-traits-typedefs.md#false_type_typedef)   
 [Definición de tipo true_type](../standard-library/type-traits-typedefs.md#true_type_typedef)


