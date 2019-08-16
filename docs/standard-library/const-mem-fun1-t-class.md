---
title: const_mem_fun1_t (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 8ccd9d7e58b9cadec83b64df5553564db20a5745
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244529"
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t (Clase)

Clase de adaptadores que permite llamar a una función miembro **const** que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de puntero. En desuso en C ++ 11, se ha quitado en C ++ 17.

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

*member_ptr*\
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

*Izquierda*\
El **const** objeto al que el *member_ptr* función miembro se llama en.

*Correcto*\
El argumento que se entrega a *member_ptr*.

## <a name="return-value"></a>Valor devuelto

Una función binaria adaptable.

## <a name="remarks"></a>Comentarios

La clase de plantilla almacena una copia de *member_ptr*, que debe ser un puntero a una función miembro de clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` que devuelva `(left->member_ptr)(right) const`.

## <a name="example"></a>Ejemplo

El constructor de `const_mem_fun1_t` no suele usarse directamente. `mem_fn` se usa para adaptar funciones miembro. Consulte [mem_fn ()](../standard-library/functional-functions.md#mem_fn) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.
