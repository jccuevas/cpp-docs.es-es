---
title: mem_fun_ref_t (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_ref_t
helpviewer_keywords:
- mem_fun_ref_t class
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
ms.openlocfilehash: d8f5ef05d1bdeec694cdf22d7e7a163478127dfc
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687768"
---
# <a name="mem_fun_ref_t-class"></a>mem_fun_ref_t (Clase)

Una clase de adaptador que permite llamar a una función miembro `non_const` que no toma ningún argumento como un objeto de función unaria cuando se inicializa con un argumento de referencia. En desuso en C++ 11, se ha quitado en C++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Result, class Type>
class mem_fun_ref_t : public unary_function<Type, Result> {
    explicit mem_fun_ref_t(
    Result (Type::* _Pm)());

    Result operator()(Type& left) const;
};
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Pm*
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

\ *izquierda*
Objeto en el que se llama a la función miembro *_Pm* .

## <a name="return-value"></a>Valor devuelto

Una función unaria adaptable.

## <a name="remarks"></a>Comentarios

La plantilla de clase almacena una copia de *_Pm*, que debe ser un puntero a una función miembro de la clase `Type`, en un objeto de miembro privado. Define su función miembro `operator()` como si devolviera (**left**. * `_Pm`) ().

## <a name="example"></a>Ejemplo

Normalmente, no se usa el constructor de `mem_fun_ref_t` directamente; la función del asistente `mem_fun_ref` se usa para adaptar funciones miembro. Vea [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.
