---
title: const_mem_fun1_ref_t (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: 76fae1ce29cb4c47870e45e8f946f6ff1fea1885
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688175"
---
# <a name="const_mem_fun1_ref_t-class"></a>const_mem_fun1_ref_t (Clase)

Clase de adaptadores que permite llamar a una función miembro **const** que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de referencia. En desuso en C++ 11, se ha quitado en C++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Result, class Type, class Arg>
    class const_mem_fun1_ref_t
        : public binary_function<Type, Arg, Result>
{
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
};
```

### <a name="parameters"></a>Parámetros

@No__t_1 *PM*
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

\ *izquierda*
Objeto **const** en el que se llama a la función miembro *PM* .

\ *derecha*
Argumento que se va a asignar a *PM*.

## <a name="return-value"></a>Valor devuelto

Una función binaria adaptable.

## <a name="remarks"></a>Comentarios

La plantilla de clase almacena una copia de *PM*, que debe ser un puntero a una función miembro de la clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` como si devuelve (`left`. \* *PM*) (`right`) **const**.

## <a name="example"></a>Ejemplo

Normalmente, no se usa el constructor de `const_mem_fun1_ref_t` directamente; la función del asistente `mem_fun_ref` se usa para adaptar funciones miembro. Vea [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) para obtener ejemplos de cómo usar adaptadores de funciones miembro.
