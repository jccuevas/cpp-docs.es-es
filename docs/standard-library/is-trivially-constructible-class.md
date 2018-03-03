---
title: Clase is_trivially_constructible | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- type_traits/std::is_trivially_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0a01ee89c1bb07ab0ca3c9c54161b7d9a3097be3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="istriviallyconstructible-class"></a>Clase is_trivially_constructible
Comprueba si un tipo se puede construir de forma trivial cuando se usan los tipos de argumento especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T, class... Args>  
struct is_trivially_constructible;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
 `Args`  
 Tipos de argumento que deben coincidir en un constructor de `T`.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo es true si el tipo `T` se puede construir de forma trivial mediante los tipos de argumento de `Args`. En caso contrario, es false. El tipo `T` se puede construir de forma trivial si la definición de variable `T t(std::declval<Args>()...);` tiene el formato correcto y se sabe que no llama a ninguna operación no trivial. Tanto `T` como todos los tipos de `Args` deben ser tipos completos, `void` o matrices de límite desconocido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)



