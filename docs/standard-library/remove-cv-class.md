---
title: remove_cv (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::remove_cv
dev_langs:
- C++
helpviewer_keywords:
- remove_cv class
- remove_cv
ms.assetid: 8502602a-1c80-479c-84e0-33bd1d6496d6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dba786f04cdb114160fd0f0388203c26bd90b41d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="removecv-class"></a>remove_cv (Clase)
Crea un tipo no cons/volatile a partir de un tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class T>  
struct remove_cv;  
 
template <class T>  
using remove_cv_t = typename remove_cv<T>::type;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a modificar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia de `remove_cv<T>` contiene un tipo modificado que es `T1` cuando `T` tiene la forma `const T1`, `volatile T1` o `const volatile T1`; de lo contrario, es `T`.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_cv_t<const volatile int> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_cv_t<const volatile int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
remove_cv_t<const volatile int> == int  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)   
 [remove_const (Clase)](../standard-library/remove-const-class.md)   
 [remove_volatile (Clase)](../standard-library/remove-volatile-class.md)
