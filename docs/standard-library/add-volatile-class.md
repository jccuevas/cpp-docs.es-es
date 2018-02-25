---
title: add_volatile (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::add_volatile
dev_langs:
- C++
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0425a4b9832b21b0b77c1f2098e9b9d359da7b91
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="addvolatile-class"></a>add_volatile (Clase)
Crea un tipo volátil a partir del tipo especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Ty>  
struct add_volatile;  
 
template <class T>
using add_volatile_t = typename add_volatile<T>::type;  
```  
  
### <a name="parameters"></a>Parámetros  
*T*  
Tipo que se va a modificar.  
  
## <a name="remarks"></a>Comentarios  
Una instancia de `add_volatile<T>` tiene un typedef de miembro `type` que es *T* si *T* es una referencia, una función o un tipo calificado como volátil; si no, es `volatile` *T*. El alias `add_volatile_t` es un acceso directo para acceder al typedef de miembro `type`. 
  
## <a name="example"></a>Ejemplo  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
{   
    std::add_volatile_t<int> *p = (volatile int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_volatile<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
} 
```  
  
```Output  
add_volatile<int> == int  
```  
  
## <a name="requirements"></a>Requisitos  

**Encabezado:** \<type_traits>  
  
**Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
[<type_traits>](../standard-library/type-traits.md)   
[remove_volatile (Clase)](../standard-library/remove-volatile-class.md)
