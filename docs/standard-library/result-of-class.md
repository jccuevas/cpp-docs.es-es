---
title: result_of (Clase) | Microsoft Docs
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
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
dev_langs:
- C++
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 08e4fc22725962d06bee35ed1adf63e3c9230ced
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="resultof-class"></a>result_of (Clase)
Determina el tipo de valor devuelto del tipo que se puede llamar que toma los tipos de argumento especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class>  
struct result_of; // Causes a static assert  
  
template <class Fn, class... ArgTypes>  
struct result_of<Fn(ArgTypes...)>;

// Helper type  
template<class T>
   using result_of_t = typename result_of<T>::type;
```  
  
#### <a name="parameters"></a>Parámetros  
 `Fn`  
 El tipo que se puede llamar para la consulta.  
  
 `ArgTypes`  
 Los tipos de la lista de argumentos para el tipo que se puede llamar para la consulta.  
  
## <a name="remarks"></a>Comentarios  
 Use esta plantilla para determinar en tiempo de compilación el tipo de resultado de `Fn`(`ArgTypes`), donde `Fn` es un tipo que se puede llamar, la referencia a la función o la referencia al tipo que se puede llamar, invocado mediante una lista de argumentos de los tipos de `ArgTypes`. El miembro `type` de la clase de plantilla menciona el tipo de resultado de `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` si la expresión no evaluada `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` tiene el formato correcto. De lo contrario, la clase de plantilla no tiene ningún miembro `type`. El tipo `Fn` y todos los tipos en el paquete de parámetros `ArgTypes` deben ser tipos completos, `void` o matrices de límite desconocido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




