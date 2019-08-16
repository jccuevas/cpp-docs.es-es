---
title: mem_fun1_ref_t (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_ref_t
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
ms.openlocfilehash: 88ab2c436b3dd3b5a289124e73b6f1b5d21f96a5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243865"
---
# <a name="memfun1reft-class"></a>mem_fun1_ref_t (Clase)

Clase de adaptadores que permite un `non_const` función miembro que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de referencia. En desuso en C ++ 11, se ha quitado en C ++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_ref_t : public binary_function<Type, Arg, Result> {
    explicit mem_fun1_ref_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type& left,
    Arg right) const;
};
```

### <a name="parameters"></a>Parámetros

*_Pm*\
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

*Izquierda*\
El objeto que la *_Pm* función miembro se llama en.

*Correcto*\
El argumento que se entrega a *_Pm*.

## <a name="return-value"></a>Valor devuelto

Una función binaria adaptable.

## <a name="remarks"></a>Comentarios

La clase de plantilla almacena una copia de *_Pm*, que debe ser un puntero a una función miembro de clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` que devuelva (**izquierdo**.\* `_Pm`) (**derecho**).

## <a name="example"></a>Ejemplo

Normalmente, no se usa el constructor de `mem_fun1_ref_t` directamente; la función del asistente `mem_fun_ref` se usa para adaptar funciones miembro. Vea [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.
