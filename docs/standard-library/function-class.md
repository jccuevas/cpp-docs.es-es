---
title: function (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
dev_langs:
- C++
helpviewer_keywords:
- std::function [C++]
- std::function [C++], result_type
- std::function [C++], assign
- std::function [C++], swap
- std::function [C++], target
- std::function [C++], target_type
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 879999f279493c10509900c040ca6f5171c215b4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="function-class"></a>function (Clase)

Contenedor para un objeto al que se puede llamar.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Fty>
class function  // Fty of type Ret(T1, T2, ..., TN)
    : public unary_function<T1, Ret>       // when Fty is Ret(T1)
    : public binary_function<T1, T2, Ret>  // when Fty is Ret(T1, T2)
{
public:
    typedef Ret result_type;

    function();
    function(nullptr_t);
    function(const function& right);
    template <class Fty2>
        function(Fty2 fn);
    template <class Fty2, class Alloc>
        function(reference_wrapper<Fty2>, const Alloc& Ax);

    template <class Fty2, class Alloc>
        void assign(Fty2, const Alloc& Ax);
    template <class Fty2, class Alloc>
        void assign(reference_wrapper<Fty2>, const Alloc& Ax);
    function& operator=(nullptr_t);
    function& operator=(const function&);
    template <class Fty2>
        function& operator=(Fty2);
    template <class Fty2>
        function& operator=(reference_wrapper<Fty2>);

    void swap(function&);
    explicit operator bool() const;

    result_type operator()(T1, T2, ....., TN) const;
    const std::type_info& target_type() const;
    template <class Fty2>
        Fty2 *target();

    template <class Fty2>
        const Fty2 *target() const;

    template <class Fty2>
        void operator==(const Fty2&) const = delete;
    template <class Fty2>
        void operator!=(const Fty2&) const = delete;
};
```

### <a name="parameters"></a>Parámetros

`Fty` El tipo de función que va a contener.

`Ax` La función de asignador.

## <a name="remarks"></a>Comentarios

La clase de plantilla es un contenedor de llamadas cuya signatura de llamada es `Ret(T1, T2, ..., TN)`. Úselo para incluir una variedad de objetos a los que se puede llamar en un contenedor uniforme.

Algunas funciones miembro toman un operando que designa el objeto de destino deseado. Puede especificar ese operando de varias maneras:

`fn`: el objeto `fn` al que se puede llamar; después de la llamada, el objeto `function` contiene una copia de `fn`

`fnref`: el objeto al que se puede llamar denominado por `fnref.get()`; después de la llamada, el objeto `function` contiene una referencia a `fnref.get()`

`right`: el objeto al que se puede llamar, de haberlo, mantenido por el objeto `function` `right`

`npc`: un puntero nulo; después de la llamada, el objeto `function` está vacío

En todos los casos, `INVOKE(f, t1, t2, ..., tN)`, donde `f` es el objeto al que se puede llamar y `t1, t2, ..., tN` son valores L de tipos `T1, T2, ..., TN` respectivamente, debe tener un formato correcto y, si `Ret` no es void, debe poder convertirse a `Ret`.

Un objeto `function` vacío no contiene ningún objeto al que se puede llamar ni ninguna referencia a un objeto al que se puede llamar.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[function](#function)|Crea un contenedor que está vacío o almacena un objeto al que se puede llamar de tipo arbitrario con una signatura fija.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[result_type](#result_type)|El tipo de valor devuelto del objeto al que se puede llamar almacenado.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[assign](#assign)|Asigna un objeto al que se puede llamar a este objeto de función.|
|[swap](#swap)|Intercambia dos objetos a los que se puede llamar.|
|[target](#target)|Comprueba si se puede llamar al objeto al que se puede llamar según lo especificado.|
|[target_type](#target_type)|Obtiene información de tipo en el objeto al que se puede llamar.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[function::operator unspecified](#op_unspecified)|Comprueba si existe un objeto al que se puede llamar almacenado.|
|[function::operator()](#op_call)|Llama a un objeto al que se puede llamar.|
|[function::operator=](#op_eq)|Reemplaza el objeto al que se puede llamar almacenado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<functional>

**Espacio de nombres:** std

## <a name="assign"></a>  function::assign

Asigna un objeto al que se puede llamar a este objeto de función.

```cpp
template <class Fx, class Alloc>
    void assign(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    void assign(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>Parámetros

`_Func` Un objeto que se puede llamar.

`_Fnref` Un contenedor de referencia que contiene un objeto que se puede llamar.

`Ax` Un objeto de asignador.

### <a name="remarks"></a>Comentarios

Las funciones miembro reemplazan al `callable object` mantenido por `*this` por el objeto al que se puede llamar pasado como el `operand`. Ambas asignan almacenamiento con el objeto de asignador `Ax`.

## <a name="function"></a>  function::function

Crea un contenedor que está vacío o almacena un objeto al que se puede llamar de tipo arbitrario con una signatura fija.

```cpp
function();
function(nullptr_t npc);
function(const function& right);
template <class Fx>
    function(Fx _Func);
template <class Fx>
    function(reference_wrapper<Fx> _Fnref);
template <class Fx, class Alloc>
    function(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    function(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>Parámetros

`right` Objeto de función que se va a copiar.

`Fx` El tipo del objeto que se puede llamar.

`_Func` El objeto que se puede llamar a ajustar.

`Alloc` El tipo de asignador.

`Ax` El asignador.

`_Fnref` La referencia de objeto que se puede llamar a ajustar.

### <a name="remarks"></a>Comentarios

Los dos primeros constructores crean un objeto `function` vacío. Los siguientes tres constructores crean un objeto `function` que contiene el objeto al que se puede llamar que ha pasado como el operando. Los dos últimos constructores asignan almacenamiento con el objeto de asignador Ax.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__function_function.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <vector>

int square(int val)
{
    return val * val;
}

class multiply_by
{
public:
    explicit multiply_by(const int n) : m_n(n) { }

    int operator()(const int x) const
    {
        return m_n * x;
    }

private:
    int m_n;
};

int main()
{

    typedef std::vector< std::function<int (int)> > vf_t;

    vf_t v;
    v.push_back(square);
    v.push_back(std::negate<int>());
    v.push_back(multiply_by(3));

    for (vf_t::const_iterator i = v.begin(); i != v.end(); ++i)
    {
        std::cout << (*i)(10) << std::endl;
    }

    std::function<int (int)> f = v[0];
    std::function<int (int)> g;

    if (f) {
        std::cout << "f is non-empty (correct)." << std::endl;
    } else {
        std::cout << "f is empty (can't happen)." << std::endl;
    }

    if (g) {
        std::cout << "g is non-empty (can't happen)." << std::endl;
    } else {
        std::cout << "g is empty (correct)." << std::endl;
    }

    return 0;
}
```

```Output
100
-10
30
f is non-empty (correct).
g is empty (correct).
```

## <a name="op_unspecified"></a>  function::operator unspecified

Comprueba si existe un objeto al que se puede llamar almacenado.

```cpp
operator unspecified();
```

### <a name="remarks"></a>Comentarios

El operador devuelve un valor que se puede convertir a `bool` con un valor true solo si el objeto no está vacío. Úselo para comprobar si el objeto está vacío.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__function_operator_bool.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == " << (bool)fn0 << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == " << (bool)fn1 << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```

## <a name="op_call"></a>  function::operator()

Llama a un objeto al que se puede llamar.

```cpp
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```

### <a name="parameters"></a>Parámetros

`TN` El tipo del enésimo llame al argumento.

`tN` El argumento n-ésima de llamada.

### <a name="remarks"></a>Comentarios

La función miembro devuelve `INVOKE(fn, t1, t2, ..., tN, Ret)`, donde `fn` es el objeto de destino almacenado en `*this`. Úsela para llamar al objeto encapsulado al que se puede llamar.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__function_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="op_eq"></a>  function::operator=

Reemplaza el objeto al que se puede llamar almacenado.

```cpp
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>
    function& operator=(Fty fn);
template <class Fty>
    function& operator=(reference_wrapper<Fty> fnref);
```

### <a name="parameters"></a>Parámetros

`npc` Una constante de puntero nulo.

`right` Objeto de función que se va a copiar.

`fn` El objeto que se puede llamar a ajustar.

`fnref` La referencia de objeto que se puede llamar a ajustar.

### <a name="remarks"></a>Comentarios

Los operadores reemplazan el objeto al que se puede llamar mantenido por `*this` por el objeto al que se puede llamar pasado como el operando.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__function_operator_as.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "val == " << fn0(3) << std::endl;

    std::function<int (int)> fn1;
    fn1 = 0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    fn1 = neg;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = fn0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = std::cref(fn1);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true
empty == false
val == -3
empty == false
val == -3
empty == false
val == -3
```

## <a name="result_type"></a>  function::result_type

El tipo de valor devuelto del objeto al que se puede llamar almacenado.

```cpp
typedef Ret result_type;
```

### <a name="remarks"></a>Comentarios

Typedef es un sinónimo del tipo `Ret` en la signatura de llamada de la plantilla. Úselo para determinar el tipo de valor devuelto del objeto encapsulado al que se puede llamar.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__function_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    std::function<int (int)>::result_type val = fn1(3);
    std::cout << "val == " << val << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="swap"></a>  function::swap

Intercambia dos objetos a los que se puede llamar.

```cpp
void swap(function& right);
```

### <a name="parameters"></a>Parámetros

`right` Objeto de función que se va a intercambiar con.

### <a name="remarks"></a>Comentarios

La función miembro intercambia los objetos de destino entre `*this` y `right`. Lo hace en tiempo constante y no inicia ninguna excepción.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__function_swap.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "val == " << fn0(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << std::endl;

    fn0.swap(fn1);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true

empty == true
empty == false
val == -3
```

## <a name="target"></a>  function::target

Comprueba si se puede llamar al objeto al que se puede llamar según lo especificado.

```cpp
template <class Fty2>
    Fty2 *target();
template <class Fty2>
    const Fty2 *target() const;
```

### <a name="parameters"></a>Parámetros

`Fty2` El tipo de objeto que se puede llamar de destino para probar.

### <a name="remarks"></a>Comentarios

Los tipos de argumento `T1, T2, ..., TN` y el tipo de valor devuelto `Ret` deben poder llamar al tipo `Fty2`. Si `target_type() == typeid(Fty2)`, la función de plantilla miembro devuelve la dirección del objeto de destino; de lo contrario, devuelve 0.

Los tipos de argumento `T1, T2, ..., TN` y el tipo de valor devuelto `Ret` pueden llamar a un tipo `Fty2` si, para los valores L `fn, t1, t2, ..., tN` de los tipos `Fty2, T1, T2, ..., TN`, respectivamente, `INVOKE(fn, t1, t2, ..., tN)` tiene el formato correcto y, si `Ret` no es `void`, se puede convertir en `Ret`.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__function_target.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    typedef int (*Myfun)(int);
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "no target == " << (fn0.target<Myfun>() == 0) << std::endl;

    Myfun *fptr = fn0.target<Myfun>();
    std::cout << "val == " << (*fptr)(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "no target == " << (fn1.target<Myfun>() == 0) << std::endl;

    return (0);
    }

```

```Output
empty == false
no target == false
val == -3
empty == true
no target == true
```

## <a name="target_type"></a>  function::target_type

Obtiene información de tipo en el objeto al que se puede llamar.

```cpp
const std::type_info& target_type() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve `typeid(void)` si `*this` está vacío; de lo contrario, devuelve `typeid(T)`, donde `T` es el tipo del objeto de destino.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__function_target_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "type == " << fn0.target_type().name() << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "type == " << fn1.target_type().name() << std::endl;

    return (0);
    }
```

```Output
empty == false
type == int (__cdecl*)(int)
empty == true
type == void
```

## <a name="see-also"></a>Vea también

[mem_fn](../standard-library/functional-functions.md#mem_fn)<br/>
[reference_wrapper (Clase)](../standard-library/reference-wrapper-class.md)<br/>
