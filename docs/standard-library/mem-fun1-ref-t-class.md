---
title: mem_fun1_ref_t (Clase)
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::mem_fun1_ref_t
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
ms.openlocfilehash: 4169ac00cfeeb2bd9f38ef0e7eb30da819fbff5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488067"
---
# <a name="memfun1reft-class"></a>mem_fun1_ref_t (Clase)

Clase de adaptadores que permite un `non_const` función miembro que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de referencia.

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

*_Pm*<br/>
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

*left*<br/>
El objeto que la *_Pm* función miembro se llama en.

*right*<br/>
El argumento que se entrega a *_Pm*.

## <a name="return-value"></a>Valor devuelto

Una función binaria adaptable.

## <a name="remarks"></a>Comentarios

La clase de plantilla almacena una copia de *_Pm*, que debe ser un puntero a una función miembro de clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` que devuelva ( **izquierdo**.\* `_Pm`) ( **derecho**).

## <a name="example"></a>Ejemplo

Normalmente, no se usa el constructor de `mem_fun1_ref_t` directamente; la función del asistente `mem_fun_ref` se usa para adaptar funciones miembro. Vea [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<functional>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
