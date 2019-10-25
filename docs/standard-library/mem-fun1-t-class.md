---
title: mem_fun1_t (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: 00d9322a8f0530da2e48b3f16fb52c00f9d1b075
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687731"
---
# <a name="mem_fun1_t-class"></a>mem_fun1_t (Clase)

Una clase de adaptadores que permite llamar a una función miembro `non_const` que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de puntero. En desuso en C++ 11, se ha quitado en C++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;
};
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Pm*
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

@No__t_1 *_Pleft*
Objeto en el que se llama a la función miembro *_Pm* .

\ *derecha*
El argumento que se asigna a *_Pm*.

## <a name="return-value"></a>Valor devuelto

Una función binaria adaptable.

## <a name="remarks"></a>Comentarios

La plantilla de clase almacena una copia de *_Pm*, que debe ser un puntero a una función miembro de la clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` como si devuelve ( **_Pleft** -> \* `_Pm`) (**right**).

## <a name="example"></a>Ejemplo

Normalmente, no se usa el constructor de `mem_fun1_t` directamente; la función del asistente `mem_fun` se usa para adaptar funciones miembro. Vea [mem_fun](../standard-library/functional-functions.md#mem_fun) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.
