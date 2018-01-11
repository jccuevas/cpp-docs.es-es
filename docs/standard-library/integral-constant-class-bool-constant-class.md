---
title: integral_constant (Clase), bool_constant (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
dev_langs: C++
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f694e763bb9fce65a703e8852e3f875a646f10c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
 [false_type](../standard-library/type-traits-typedefs.md#false_type)   
 [true_type](../standard-library/type-traits-typedefs.md#true_type)

