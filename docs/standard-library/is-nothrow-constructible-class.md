---
title: Clase is_nothrow_constructible | Microsoft Docs
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
- is_nothrow_constructible
- type_traits/std::is_nothrow_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
caps.latest.revision: 12
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: bf39b973c39fd024de6b4b75b3cc47aeb5bec9d8
ms.lasthandoff: 02/24/2017

---
# <a name="isnothrowconstructible-class"></a>Clase is_nothrow_constructible
Comprueba si un tipo se puede construir y se sabe que no se inicia cuando se usan los tipos de argumento especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T, class... Args>  
struct is_nothrow_constructible;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
 `Args`  
 Tipos de argumento que deben coincidir en un constructor de `T`.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo es true si el tipo `T` se puede construir mediante los tipos de argumento de `Args` y el compilador sabe que el constructor no se inicia. En caso contrario, es false. El tipo `T` se puede construir si la definición de variable `T t(std::declval<Args>()...);` tiene el formato correcto. Tanto `T` como todos los tipos de `Args` deben ser tipos completos, `void` o matrices de límite desconocido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




