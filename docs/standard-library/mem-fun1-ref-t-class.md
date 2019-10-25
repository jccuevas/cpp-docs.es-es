---
title: mem_fun1_ref_t (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_ref_t
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
ms.openlocfilehash: 238d6147b2afa5ca3e143bc57aa4892e17d2c869
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687755"
---
# <a name="mem_fun1_ref_t-class"></a>mem_fun1_ref_t (Clase)

Una clase de adaptadores que permite llamar a una función miembro `non_const` que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de referencia. En desuso en C++ 11, se ha quitado en C++ 17.

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

@No__t_1 *_Pm*
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

\ *izquierda*
Objeto en el que se llama a la función miembro *_Pm* .

\ *derecha*
El argumento que se asigna a *_Pm*.

## <a name="return-value"></a>Valor devuelto

Una función binaria adaptable.

## <a name="remarks"></a>Comentarios

La plantilla de clase almacena una copia de *_Pm*, que debe ser un puntero a una función miembro de la clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` como si devuelve (**left**. \* `_Pm`) (**right**).

## <a name="example"></a>Ejemplo

Normalmente, no se usa el constructor de `mem_fun1_ref_t` directamente; la función del asistente `mem_fun_ref` se usa para adaptar funciones miembro. Vea [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.
