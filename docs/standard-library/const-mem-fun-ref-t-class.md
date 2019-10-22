---
title: const_mem_fun_ref_t (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_ref_t
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
ms.openlocfilehash: 8ce29eb0d2122dbd95fea34fa59f3fa11b9b388e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689760"
---
# <a name="const_mem_fun_ref_t-class"></a>const_mem_fun_ref_t (Clase)

Clase de adaptadores que permite llamar a una función miembro **const** que no toma ningún argumento como un objeto de función unaria cuando se inicializa con un argumento de referencia. En desuso en C++ 11, se ha quitado en C++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Result, class Type>
    class const_mem_fun_ref_t
: public unary_function<Type, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type& left) const;
};
```

### <a name="parameters"></a>Parámetros

@No__t_1 *PM*
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

\ *izquierda*
Objeto en el que se llama a la función miembro *PM* .

## <a name="return-value"></a>Valor devuelto

Una función unaria adaptable.

## <a name="remarks"></a>Comentarios

La plantilla de clase almacena una copia de *PM*, que debe ser un puntero a una función miembro de la clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` como si devuelve (**left**. \* `Pm`) () **const**.

## <a name="example"></a>Ejemplo

Normalmente, no se usa el constructor de `const_mem_fun_ref_t` directamente; la función del asistente `mem_fun_ref` se usa para adaptar funciones miembro. Vea [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.
