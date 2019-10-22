---
title: const_mem_fun_t (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_t
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
ms.openlocfilehash: 5263612a26b2bcb606ad712a2a8e0a521ce9437a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688208"
---
# <a name="const_mem_fun_t-class"></a>const_mem_fun_t (Clase)

Clase de adaptadores que permite llamar a una función miembro const que no toma ningún argumento como un objeto de función unaria cuando se inicializa con un argumento de referencia. En desuso en C++ 11, se ha quitado en C++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Result, class Type>
class const_mem_fun_t : public unary_function <Type *, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type* Pleft) const;
};
```

### <a name="parameters"></a>Parámetros

@No__t_1 *PM*
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

@No__t_1 *Pleft*
Objeto en el que se llama a la función miembro *PM* .

## <a name="return-value"></a>Valor devuelto

Una función unaria adaptable.

## <a name="remarks"></a>Comentarios

La plantilla de clase almacena una copia de *PM*, que debe ser un puntero a una función miembro de la clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` como si devuelve (`Pleft` -> \* `Pm`) () **const**.

## <a name="example"></a>Ejemplo

Normalmente, no se usa el constructor de `const_mem_fun_t` directamente; la función del asistente `mem_fun` se usa para adaptar funciones miembro. Vea [mem_fun](../standard-library/functional-functions.md#mem_fun) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.
