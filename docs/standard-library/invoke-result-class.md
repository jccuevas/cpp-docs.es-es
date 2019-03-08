---
title: Clase invoke_result
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: 7c03240d3ee666fcda30562279a8dbda2ca8dc7b
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006876"
---
# <a name="invokeresult-class"></a>Clase invoke_result

Determina el tipo de valor devuelto del tipo que se puede llamar que toma los tipos de argumento especificado en tiempo de compilación. Agregado en C ++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Parámetros

*Callable*<br/>
El tipo que se puede llamar para la consulta.

*Args*<br/>
Los tipos de la lista de argumentos para el tipo que se puede llamar para la consulta.

## <a name="remarks"></a>Comentarios

Use esta plantilla para determinar el tipo de resultado de *Callable*(*Args*...) en tiempo de compilación, donde *Callable* y todos los tipos de *Args* son cualquier tipo completa, una matriz de límite desconocido o una posiblemente cv calificado `void`. El `type` el tipo de valor devuelto de los nombres de miembro de la clase de plantilla *Callable* cuando se invoca utilizando los argumentos *Args*... El `type` sólo se define un miembro si *Callable* se puede llamar cuando se invoca utilizando los argumentos *Args*... en un contexto no evaluado. En caso contrario, la clase de plantilla no tiene ningún miembro `type`, lo que permite SFINAE pruebas en un conjunto determinado de tipos de argumento en tiempo de compilación.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke](functional-functions.md#invoke)
