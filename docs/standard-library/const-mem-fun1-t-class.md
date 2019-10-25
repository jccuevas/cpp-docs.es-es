---
title: const_mem_fun1_t (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 1af44635400037c6359b13c4f2925c3ac7f2d9d5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689750"
---
# <a name="const_mem_fun1_t-class"></a>const_mem_fun1_t (Clase)

Clase de adaptadores que permite llamar a una función miembro **const** que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de puntero. En desuso en C++ 11, se ha quitado en C++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* member_ptr)(Arg) const);
    Result operator()(const Type* left, Arg right) const;
};
```

### <a name="parameters"></a>Parámetros

\ *member_ptr*
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

\ *izquierda*
El objeto **const** en el que se llama a la función miembro *member_ptr* .

\ *derecha*
El argumento que se asigna a *member_ptr*.

## <a name="return-value"></a>Valor devuelto

Una función binaria adaptable.

## <a name="remarks"></a>Comentarios

La plantilla de clase almacena una copia de *member_ptr*, que debe ser un puntero a una función miembro de la clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` como si devolviera `(left->member_ptr)(right) const`.

## <a name="example"></a>Ejemplo

El constructor de `const_mem_fun1_t` no suele usarse directamente. `mem_fn` se utiliza para adaptar las funciones miembro. Vea [mem_fn](../standard-library/functional-functions.md#mem_fn) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.
