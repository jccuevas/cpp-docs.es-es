---
title: pointer_to_binary_function (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: 88d38be258c6ceb1054e0d31cc52e4d8d25186ec
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006804"
---
# <a name="pointertobinaryfunction-class"></a>pointer_to_binary_function (Clase)

Convierte un puntero a función binaria en una función binaria adaptable. En desuso en C ++ 11, se ha quitado en C ++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
public:
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>Parámetros

*pfunc*<br/>
La función binaria que se va a convertir.

*left*<br/>
El objeto de la izquierda al que *\*pfunc* está llamado.

*right*<br/>
El objeto de la derecha al que *\*pfunc* está llamado.

## <a name="return-value"></a>Valor devuelto

La clase de plantilla almacena una copia de `pfunc`. Define su función miembro `operator()` que devuelva `(* pfunc)(Left, right)`.

## <a name="remarks"></a>Comentarios

Un puntero de función binaria es un objeto de función y puede pasarse a cualquier algoritmo de la biblioteca estándar de C++ que esté esperando una función binaria como un parámetro, pero no es adaptable. Para usarlo con un adaptador, por ejemplo al enlazar un valor a este o usándolo con un negador, debe proporcionarse con los tipos anidados `first_argument_type`, `second_argument_type`, y `result_type` que hacen posible dicha adaptación. La conversión mediante `pointer_to_binary_function` permite a los adaptadores de función que funcionen con punteros de función binaria.

## <a name="example"></a>Ejemplo

El constructor de `pointer_to_binary_function` no suele usarse directamente. Vea la función del asistente [ptr_fun](../standard-library/functional-functions.md#ptr_fun) para obtener un ejemplo de cómo declarar y usar el predicador del adaptador de `pointer_to_binary_function`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<functional>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
