---
title: mem_fun_t (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_t
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
ms.openlocfilehash: 3c6606fe4d2df3b6068c3bb8194dc380344f7d97
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689380"
---
# <a name="mem_fun_t-class"></a>mem_fun_t (Clase)

Una clase de adaptador que permite llamar a una función miembro `non_const` que no toma ningún argumento como un objeto de función unaria cuando se inicializa con un argumento de puntero. En desuso en C++ 11, se ha quitado en C++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;
};
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Pm*
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

@No__t_1 *_Pleft*
Objeto en el que se llama a la función miembro *_Pm* .

## <a name="return-value"></a>Valor devuelto

Una función unaria adaptable.

## <a name="remarks"></a>Comentarios

La plantilla de clase almacena una copia de *_Pm*, que debe ser un puntero a una función miembro de la clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` como si devuelve (`_Pleft` ->*  `_Pm`) ().

## <a name="example"></a>Ejemplo

Normalmente, no se usa el constructor de `mem_fun_t` directamente; la función del asistente `mem_fun` se usa para adaptar funciones miembro. Vea [mem_fun](../standard-library/functional-functions.md#mem_fun) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.
