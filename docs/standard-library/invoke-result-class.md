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
ms.openlocfilehash: 8cd72e62fcb65209482fd9677afcc2ec83356feb
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689519"
---
# <a name="invoke_result-class"></a>Clase invoke_result

Determina el tipo de valor devuelto del tipo al que se puede llamar que toma los tipos de argumento especificados en tiempo de compilación. Agregado en C++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Parámetros

@No__t_1 *invocable*
El tipo que se puede llamar para la consulta.

@No__t_1 *args*
Los tipos de la lista de argumentos para el tipo que se puede llamar para la consulta.

## <a name="remarks"></a>Comentarios

Use esta plantilla para determinar el tipo de resultado de *Callable*(*args*...) en tiempo de compilación, donde se *puede llamar* y todos los tipos de *args* son de cualquier tipo completo, una matriz de enlazada desconocida o una `void` posiblemente calificada como CV. El miembro `type` de la plantilla de clase nombra el tipo de valor devuelto al que se *puede llamar* cuando se invoca mediante los argumentos *args*.... El miembro `type` solo se define si se puede llamar a *Callable* cuando se invoca mediante los argumentos *args*... en un contexto no evaluado. De lo contrario, la plantilla de clase no tiene `type` miembro, lo que permite pruebas SFINAE en un conjunto determinado de tipos de argumento en tiempo de compilación.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[vocó](functional-functions.md#invoke)
