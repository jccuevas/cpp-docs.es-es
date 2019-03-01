---
title: result_of (Clase)
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
ms.openlocfilehash: f60a3ef6528da33fd1117fc940e961e9fe0987df
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006557"
---
# <a name="resultof-class"></a>result_of (Clase)

Determina el tipo de valor devuelto del tipo que se puede llamar que toma los tipos de argumento especificados. Agregado en C ++ 14, en desuso en C ++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template<class>
struct result_of; // Causes a static assert

template <class Fn, class... ArgTypes>
struct result_of<Fn(ArgTypes...)>;

// Helper type
template<class T>
   using result_of_t = typename result_of<T>::type;
```

### <a name="parameters"></a>Parámetros

*Fn*<br/>
El tipo que se puede llamar para la consulta.

*ArgTypes*<br/>
Los tipos de la lista de argumentos para el tipo que se puede llamar para la consulta.

## <a name="remarks"></a>Comentarios

Use esta plantilla para determinar en tiempo de compilación, el tipo de resultado de `Fn`(`ArgTypes`), donde *Fn* es un tipo que se puede llamar, una referencia a función o una referencia al tipo que se puede llamar, invocado mediante una lista de argumentos de los tipos en  *ArgTypes*. El miembro `type` de la clase de plantilla menciona el tipo de resultado de `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` si la expresión no evaluada `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` tiene el formato correcto. De lo contrario, la clase de plantilla no tiene ningún miembro `type`. El tipo *Fn* y todos los tipos en el paquete de parámetros *ArgTypes* deben ser tipos completos, **void**, o matrices de límite desconocido. En desuso en favor de [invoke_result](invoke-result-class.md) en C ++ 17.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[clase invoke_result](invoke-result-class.md)<br/>
