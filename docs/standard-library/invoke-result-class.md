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
ms.openlocfilehash: 2b2051b0c854151cff9b439f5ec0a951c25a6387
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447639"
---
# <a name="invokeresult-class"></a>Clase invoke_result

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

*Llamadas*\
El tipo que se puede llamar para la consulta.

*Args*\
Los tipos de la lista de argumentos para el tipo que se puede llamar para la consulta.

## <a name="remarks"></a>Comentarios

Utilice esta plantilla para determinar el tipo de resultado de Callable (*args*...) en tiempo de compilación, donde se *puede llamar* a y todos los tipos de *args* son de tipo completo, una matriz de límite desconocido `void`o un posible calificado con la VC. El `type` miembro de la clase de plantilla denomina el tipo de valor devuelto al que se *puede llamar* cuando se invoca mediante los argumentos *args*.... El `type` miembro solo se define si  se puede llamar a Callable cuando se invoca mediante los argumentos *args*... en un contexto no evaluado. De lo contrario, la clase de plantilla `type`no tiene ningún miembro, lo que permite pruebas SFINAE en un conjunto determinado de tipos de argumento en tiempo de compilación.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
