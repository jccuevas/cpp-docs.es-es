---
title: mem_fun1_t (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: 822de97849750a72948137ba8fe23beab8554ff5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245098"
---
# <a name="memfun1t-class"></a>mem_fun1_t (Clase)

Clase de adaptadores que permite un `non_const` función miembro que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de puntero. En desuso en C ++ 11, se ha quitado en C ++ 17.

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

*_Pm*\
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

*_Pleft*\
El objeto que la *_Pm* función miembro se llama en.

*Correcto*\
El argumento que se entrega a *_Pm*.

## <a name="return-value"></a>Valor devuelto

Una función binaria adaptable.

## <a name="remarks"></a>Comentarios

La clase de plantilla almacena una copia de *_Pm*, que debe ser un puntero a una función miembro de clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` que devuelva ( **_Pleft** -> \* `_Pm`) (**derecho**).

## <a name="example"></a>Ejemplo

Normalmente, no se usa el constructor de `mem_fun1_t` directamente; la función del asistente `mem_fun` se usa para adaptar funciones miembro. Vea [mem_fun](../standard-library/functional-functions.md#mem_fun) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.
