---
title: Clase is_trivially_copy_assignable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_trivially_copy_assignable
- std.is_trivially_copy_assignable
- std::is_trivially_copy_assignable
- type_traits/std::is_trivially_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.openlocfilehash: 97935fed1736f111557a0cb86811a86d60505107
ms.lasthandoff: 02/24/2017

---
# <a name="istriviallycopyassignable-class"></a>Clase is_trivially_copy_assignable
Comprueba si el tipo tiene un operador de asignación de copia trivial.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty>
struct is_trivially_copy_assignable;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `T` es una clase que tiene un operador de asignación de copias trivial; en caso contrario, contiene false.  
  
 Un constructor de asignación para una clase `T` es trivial si se proporciona implícitamente, la clase `T` no tiene ninguna función virtual, la clase `T` no tiene ninguna base virtual, las clases de todos los miembros de datos no estáticos de tipo de clase tienen operadores de asignación triviales y las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación triviales.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




