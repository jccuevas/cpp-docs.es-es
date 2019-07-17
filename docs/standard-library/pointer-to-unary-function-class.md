---
title: pointer_to_unary_function (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: cff84f1f15eea34c60162f702dfe05350d1383d1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240462"
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function (Clase)

Convierte un puntero a función unaria en una función unaria adaptable. En desuso en C ++ 11, se ha quitado en C ++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>Parámetros

*pfunc*\
La función binaria que se va a convertir.

*Izquierda*\
El objeto al que *\*pfunc* está llamado.

## <a name="return-value"></a>Valor devuelto

La clase de plantilla almacena una copia de `pfunc`. Define su función miembro `operator()` para que devuelva (\* **pfunc**)(_ *Left*).

## <a name="remarks"></a>Comentarios

Un puntero de función unaria es un objeto de función y puede pasarse a cualquier algoritmo de la biblioteca estándar de C++ que esté esperando una función unaria como un parámetro, pero no es adaptable. Para usarlo con un adaptador, por ejemplo al enlazar un valor a este o usándolo con un negador, debe proporcionarse con los tipos anidados `argument_type` y `result_type` que hacen posible dicha adaptación. La conversión mediante `pointer_to_unary_function` permite a los adaptadores de función que funcionen con punteros de función binaria.

## <a name="example"></a>Ejemplo

El constructor de `pointer_to_unary_function` no suele usarse directamente. Vea la función del asistente [ptr_fun](../standard-library/functional-functions.md#ptr_fun) para obtener un ejemplo de cómo declarar y usar el predicador del adaptador de `pointer_to_unary_function`.
