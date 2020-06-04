---
title: invoke_result (clase)
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: a5f67935bde103cf10c1bd9948ac1388f5221322
ms.sourcegitcommit: f38f770bfda1c174d2b81fabda7c893b15bd83a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473885"
---
# <a name="invoke_result-class"></a>invoke_result (clase)

Determina el tipo de valor devuelto del tipo al que se puede llamar que toma los tipos de argumento especificados en tiempo de compilación. Agregado en C++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<class Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Parámetros

\ *invocable*
El tipo que se puede llamar para la consulta.

\ *args*
Los tipos de la lista de argumentos para el tipo que se puede llamar para la consulta.

## <a name="remarks"></a>Observaciones

Use esta plantilla para determinar el tipo de resultado de *Callable*(*args*...) en tiempo de compilación, donde se *puede llamar* y todos los tipos de *args* son de cualquier tipo completo, una matriz de enlazada desconocida o una `void`posiblemente calificada como CV. El miembro `type` de la plantilla de clase nombra el tipo de valor devuelto al que se *puede llamar* cuando se invoca mediante los argumentos *args*.... El miembro `type` solo se define si se puede llamar a *Callable* cuando se invoca mediante los argumentos *args*... en un contexto no evaluado. De lo contrario, la plantilla de clase no tiene `type`miembro, lo que permite pruebas SFINAE en un conjunto determinado de tipos de argumento en tiempo de compilación.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits >

**Espacio de nombres:** std

## <a name="see-also"></a>Consulte también

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
