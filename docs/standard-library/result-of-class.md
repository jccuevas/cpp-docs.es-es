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
ms.openlocfilehash: ab575ac31936e7003f19fc2ceb3c5b1727d0728c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688992"
---
# <a name="result_of-class"></a>result_of (Clase)

Determina el tipo de valor devuelto del tipo que se puede llamar que toma los tipos de argumento especificados. Agregado en C++ 14, en desuso en C++ 17.

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

*Fn* \
El tipo que se puede llamar para la consulta.

@No__t_1 *ArgTypes*
Los tipos de la lista de argumentos para el tipo que se puede llamar para la consulta.

## <a name="remarks"></a>Comentarios

Use esta plantilla para determinar en tiempo de compilación el tipo de resultado de `Fn` (`ArgTypes`), donde *FN* es un tipo al que se puede llamar, una referencia a una función o una referencia a un tipo al que se puede llamar, que se invoca mediante una lista de argumentos de los tipos de *ArgTypes*. El miembro `type` de la plantilla de clase nombra el tipo de resultado de `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` si la expresión no evaluada `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` tiene el formato correcto. De lo contrario, la plantilla de clase no tiene ningún `type` de miembro. El tipo *FN* y todos los tipos en el paquete de parámetros *ArgTypes* deben ser tipos completos, **void**o matrices de enlazados desconocidos. En desuso en favor de [invoke_result](invoke-result-class.md) en c++ 17.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[clase invoke_result](invoke-result-class.md)
