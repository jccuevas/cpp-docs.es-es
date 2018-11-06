---
title: const_mem_fun_ref_t (Clase)
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::const_mem_fun_ref_t
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
ms.openlocfilehash: 3f0a87b71f39847590c5fbc4e94038b216ec4b1a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515523"
---
# <a name="constmemfunreft-class"></a>const_mem_fun_ref_t (Clase)

Clase de adaptadores que permite llamar a una función miembro **const** que no toma ningún argumento como un objeto de función unaria cuando se inicializa con un argumento de referencia.

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

*P. M.*<br/>
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

*left*<br/>
El objeto que la *Pm* función miembro se llama en.

## <a name="return-value"></a>Valor devuelto

Una función unaria adaptable.

## <a name="remarks"></a>Comentarios

La clase de plantilla almacena una copia de *Pm*, que debe ser un puntero a una función miembro de clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` que devuelva ( **izquierdo**.\* `Pm`) () **const**.

## <a name="example"></a>Ejemplo

Normalmente, no se usa el constructor de `const_mem_fun_ref_t` directamente; la función del asistente `mem_fun_ref` se usa para adaptar funciones miembro. Vea [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<functional>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
