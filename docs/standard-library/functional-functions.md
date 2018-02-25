---
title: '&lt;functional&gt; (Funciones) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- functional/std::bind
- xfunctional/std::bind1st
- xfunctional/std::bind2nd
- xfunctional/std::bit_and
- xfunctional/std::bit_not
- xfunctional/std::bit_or
- xfunctional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- xfunctional/std::mem_fn
- xfunctional/std::mem_fun_ref
- xfunctional/std::not1
- xfunctional/std::not2
- xfunctional/std::ptr_fun
- functional/std::ref
- functional/std::swap
dev_langs:
- C++
helpviewer_keywords:
- std::bind [C++]
- std::bind1st
- std::bind2nd
- std::bit_and [C++]
- std::bit_not [C++]
- std::bit_or [C++]
- std::bit_xor [C++]
- std::cref [C++]
ms.assetid: c34d0b45-50a7-447a-9368-2210d06339a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0401f97cbaa30cd0489227008195568748d24b80
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ltfunctionalgt-functions"></a>&lt;functional&gt; (Funciones)
||||  
|-|-|-|  
|[bind](#bind)|[bind1st](#bind1st)|[bind2nd](#bind2nd)|  
|[bit_and](#bit_and)|[bit_not](#bit_not)|[bit_or](#bit_or)|  
|[bit_xor](#bit_xor)|[cref](#cref)|[mem_fn](#mem_fn)|  
|[mem_fun](#mem_fun)|[mem_fun_ref](#mem_fun_ref)|[not1](#not1)|  
|[not2](#not2)|[ptr_fun](#ptr_fun)|[ref](#ref)|  
|[swap](#swap)|  
  
##  <a name="bind"></a>  bind  
 Enlaza argumentos a un objeto al que se puede llamar.  
  
```  
template <class Fty, class T1, class T2, ..., class TN>  
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);

template <class Ret, class Fty, class T1, class T2, ..., class TN>  
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);
```  
  
### <a name="parameters"></a>Parámetros  
 `Fty`  
 El tipo del objeto al que se va a llamar.  
  
 `TN`  
 Tipo del enésimo argumento de llamada.  
  
 `fn`  
 El objeto al que se va a llamar.  
  
 `tN`  
 El enésimo argumento de llamada.  
  
### <a name="remarks"></a>Comentarios  
 Los tipos `Fty, T1, T2, ..., TN` tienen que poder construirse mediante copia y `INVOKE(fn, t1, ..., tN)` debe ser una expresión válida para algunos valores `w1, w2, ..., wN`.  
  
 La primera función de plantilla devuelve un contenedor de llamadas de reenvío `g` con un tipo de resultado débil. El efecto de `g(u1, u2, ..., uM)` es `INVOKE(f, v1, v2, ..., vN, ` [result_of ()](../standard-library/result-of-class.md)`<Fty cv (V1, V2, ..., VN)>::type)`, donde `cv` es los calificadores cv de `g` y los valores y tipos de los argumentos enlazados `v1, v2, ..., vN` se determina como Especifica a continuación. Úselo para enlazar los argumentos con un objeto al que se puede llamar para crear un objeto al que se puede llamar con una lista de argumentos adaptada.  
  
 La segunda función de plantilla devuelve un contenedor de llamadas de reenvío `g` con un tipo anidado `result_type` que es un sinónimo de `Ret`. El efecto de `g(u1, u2, ..., uM)` es `INVOKE(f, v1, v2, ..., vN, Ret)`, donde `cv` son los calificadores cv de `g` y los valores y tipos de los argumentos enlazados `v1, v2, ..., vN` están determinados como se indica a continuación. Úselo para enlazar los argumentos con un objeto al que se puede llamar para crear un objeto al que se puede llamar con una lista de argumentos adaptada y con un tipo de valor devuelto especificado.  
  
 Los valores de los argumentos enlazados `v1, v2, ..., vN` y sus tipos correspondientes `V1, V2, ..., VN` dependen del tipo del argumento correspondiente `ti` de tipo `Ti` en la llamada a `bind` y los calificadores cv `cv` del contenedor de llamadas `g` de la siguiente forma:  
  
 si `ti` es de tipo `reference_wrapper<T>`, el argumento `vi` es `ti.get()` y su tipo `Vi` es `T&`;  
  
 si el valor de `std::is_bind_expression<Ti>::value` es `true`, el argumento `vi` es `ti(u1, u2, ..., uM)` y su tipo `Vi` es `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`;  
  
 si el valor `j` de `std::is_placeholder<Ti>::value` no es cero, el argumento `vi` es `uj` y su tipo `Vi` es `Uj&`;  
  
 de lo contrario, el argumento `vi` es `ti` y su tipo `Vi` es `Ti` `cv` `&`.  
  
 Por ejemplo, dada una función `f(int, int)`, la expresión `bind(f, _1, 0)` devuelve un contenedor de llamadas de reenvío `cw` de modo que `cw(x)` llama a `f(x, 0)`. La expresión `bind(f, 0, _1)` devuelve un contenedor de llamadas de reenvío `cw` de modo que `cw(x)` llama a `f(0, x)`.  
  
 El número de argumentos en una llamada a `bind` además del argumento `fn` debe ser igual al número de argumentos que se puede pasar al objeto `fn` al que se puede llamar. Por tanto, `bind(cos, 1.0)` es correcto y `bind(cos)` y `bind(cos, _1, 0.0)` son incorrectos.  
  
 El número de argumentos de la llamada de función al contenedor de llamadas devuelto por `bind` debe ser al menos tan grande como el valor numerado más alto de `is_placeholder<PH>::value` para todos los argumentos de marcador de posición en la llamada a `bind`. Por tanto, `bind(cos, _2)(0.0, 1.0)` es correcto (y devuelve `cos(1.0)`) y `bind(cos, _2)(0.0)` es incorrecto.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__functional__bind.cpp   
// compile with: /EHsc   
#include <functional>   
#include <algorithm>   
#include <iostream>   
  
using namespace std::placeholders;   
  
void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

void product(double x, double y)
{
    std::cout << x << "*" << y << " == " << x * y << std::endl;
}

int main()
{
    double arg[] = { 1, 2, 3 };

    std::for_each(&arg[0], arg + 3, square);
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(square, _1));

    return (0);
}

```  
  
```Output  
1^2 == 1  
2^2 == 4  
3^2 == 9  
  
1*2 == 2  
2*2 == 4  
3*2 == 6  
  
1^2 == 1  
2^2 == 4  
3^2 == 9  
```  
  
##  <a name="bind1st"></a>  bind1st  
 Función de plantilla auxiliar que crea un adaptador para convertir un objeto de función binaria en un objeto de función unaria enlazando el primer argumento de la función binaria a un valor especificado.  
  
```  
template <class Operation, class Type>  
binder1st <Operation> bind1st (const Operation& func, const Type& left);
```  
  
### <a name="parameters"></a>Parámetros  
 `func`  
 El objeto de función binaria que se va a convertir en un objeto de función unaria.  
  
 `left`  
 El valor al que se enlazará el primer argumento del objeto de función binaria.  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de función unaria que es el resultado de enlazar el primer argumento de objeto de función binaria en el valor `left`.  
  
### <a name="remarks"></a>Comentarios  
 Los enlazadores de función son un tipo de adaptador de función y, ya que devuelven objetos de función, se pueden usar en determinados tipos de composición de funciones para crear expresiones más complicadas y eficaces.  
  
 Si `func` es un objeto de tipo `Operation` y `c` es una constante, `bind1st` ( `func`, `c`) es equivalente al constructor de clase [binder1st](../standard-library/binder1st-class.md) `binder1st`< `Operation`> ( `func`, `c`) y es más conveniente.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// functional_bind1st.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
// Creation of a user-defined function object  
// that inherits from the unary_function base class  
class greaterthan5: unary_function<int, bool>  
{  
public:  
    result_type operator()(argument_type i)  
    {  
        return (result_type)(i > 5);  
    }  
};  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( " ;  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    // Count the number of integers > 10 in the vector  
    vector<int>::iterator::difference_type result1a;  
    result1a = count_if(v1.begin(), v1.end(), bind1st(less<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1a << "." << endl;  
  
    // Compare: counting the number of integers > 5 in the vector  
    // with a user defined function object  
    vector<int>::iterator::difference_type result1b;  
    result1b = count_if(v1.begin(), v1.end(), greaterthan5());  
    cout << "The number of elements in v1 greater than 5 is: "  
         << result1b << "." << endl;  
  
    // Count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(), bind2nd(less<int>(), 10));  
    cout << "The number of elements in v1 less than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
```Output  
The vector v1 = ( 0 5 10 15 20 25 )  
The number of elements in v1 greater than 10 is: 3.  
The number of elements in v1 greater than 5 is: 4.  
The number of elements in v1 less than 10 is: 2.  
```  
  
##  <a name="bind2nd"></a>  bind2nd  
 Función de plantilla auxiliar que crea un adaptador para convertir un objeto de función binaria en un objeto de función unaria enlazando el segundo argumento de la función binaria a un valor especificado.  
  
```  
template <class Operation, class Type>  
binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `func`  
 El objeto de función binaria que se va a convertir en un objeto de función unaria.  
  
 `right`  
 El valor al que se enlazará el segundo argumento del objeto de función binaria.  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de función unaria que es el resultado de enlazar el segundo argumento de objeto de función binaria en el valor `right`.  
  
### <a name="remarks"></a>Comentarios  
 Los enlazadores de función son un tipo de adaptador de función y, ya que devuelven objetos de función, se pueden usar en determinados tipos de composición de funciones para crear expresiones más complicadas y eficaces.  
  
 Si `func` es un objeto de tipo **Operation** y `c` es una constante, `bind2nd` ( `func`, `c` ) es equivalente al constructor de clase [binder2nd](../standard-library/binder2nd-class.md) **binder2nd\<Operation>** ( `func`, `c` ) y más conveniente.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// functional_bind2nd.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
// Creation of a user-defined function object  
// that inherits from the unary_function base class  
class greaterthan15: unary_function<int, bool>  
{  
public:  
    result_type operator()(argument_type i)  
    {  
        return (result_type)(i > 15);  
    }  
};  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    // Count the number of integers > 10 in the vector  
    vector<int>::iterator::difference_type result1a;  
    result1a = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1a << "." << endl;  
  
    // Compare counting the number of integers > 15 in the vector  
    // with a user-defined function object  
    vector<int>::iterator::difference_type result1b;  
    result1b = count_if(v1.begin(), v1.end(), greaterthan15());  
    cout << "The number of elements in v1 greater than 15 is: "  
         << result1b << "." << endl;  
  
    // Count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(), bind1st(greater<int>(), 10));  
    cout << "The number of elements in v1 less than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
```Output  
The vector v1 = ( 0 5 10 15 20 25 )  
The number of elements in v1 greater than 10 is: 3.  
The number of elements in v1 greater than 15 is: 2.  
The number of elements in v1 less than 10 is: 2.  
```  
  
##  <a name="bit_and"></a>  bit_and  
 Objeto de función predefinido que realiza la operación AND bit a bit (`operator&` binario) sobre sus argumentos.  
  
```  
template <class Type = void>  
struct bit_and : public binary_function<Type, Type, Type> {  
    Type operator()(
    const Type& Left,   
    const Type& Right) const; 
 };  
 
// specialized transparent functor for operator& 
template <>
struct bit_and<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const  ->
        decltype(std::forward<T>(Left) & std::forward<U>(Right));
};
```  
  
### <a name="parameters"></a>Parámetros  
 `Type`, `T`, `U`  
 Cualquier tipo que admite un `operator&` que toma operandos de los tipos especificados o deducidos.  
  
 `Left`  
 Operando izquierdo de la operación AND bit a bit. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `T`.  
  
 `Right`  
 Operando derecho de la operación AND bit a bit. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `U`.  
  
### <a name="return-value"></a>Valor devuelto  
 Resultado de `Left & Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator&`.  
  
### <a name="remarks"></a>Comentarios  
 El functor de `bit_and` está limitado a tipos enteros para los tipos de datos básicos, o a tipos definidos por el usuario que implementan el `operator&` binario.  
  
##  <a name="bit_not"></a>  bit_not  
 Objeto de función predefinido que realiza la operación de complemento bit a bit (NOT) (`operator~`unario) sobre su argumento.  
  
```  
template <class Type = void>  
struct bit_not : public unary_function<Type, Type>   
 {  
    Type operator()(const Type& Right) const; 
 };  
 
// specialized transparent functor for operator~  
template <>  
struct bit_not<void>   
 {  
    template <class Type>  
    auto operator()(Type&& Right) const  ->  decltype(~std::forward<Type>(Right));
 };  
```  
  
### <a name="parameters"></a>Parámetros  
 `Type`  
 Tipo que admite un `operator~` unario.  
  
 `Right`  
 Operando de la operación de complemento bit a bit. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de un argumento de referencia de valor L o valor R del tipo deducido `Type`.  
  
### <a name="return-value"></a>Valor devuelto  
 Resultado de `~ Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator~`.  
  
### <a name="remarks"></a>Comentarios  
 El functor de `bit_not` está limitado a tipos enteros para los tipos de datos básicos, o a tipos definidos por el usuario que implementan el `operator~` binario.  
  
##  <a name="bit_or"></a>  bit_or  
 Objeto de función predefinido que realiza la operación OR bit a bit (`operator|`) sobre sus argumentos.  
  
```  
template <class Type = void>  
struct bit_or : public binary_function<Type, Type, Type> {  
    Type operator()(
    const Type& Left,   
    const Type& Right) const; 
 };  
 
// specialized transparent functor for operator|  
template <>
struct bit_or<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        ->  decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```  
  
### <a name="parameters"></a>Parámetros  
 `Type`, `T`, `U`  
 Cualquier tipo que admite un `operator|` que toma operandos de los tipos especificados o deducidos.  
  
 `Left`  
 Operando izquierdo de la operación OR bit a bit. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `T`.  
  
 `Right`  
 Operando derecho de la operación OR bit a bit. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `U`.  
  
### <a name="return-value"></a>Valor devuelto  
 Resultado de `Left | Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator|`.  
  
### <a name="remarks"></a>Comentarios  
 El functor de `bit_or` está limitado a tipos enteros para los tipos de datos básicos, o a tipos definidos por el usuario que implementan el `operator|`.  
  
##  <a name="bit_xor"></a>  bit_xor  
 Objeto de función predefinido que realiza la operación XOR bit a bit (`operator^` binario) sobre sus argumentos.  
  
```  
template <class Type = void>  
struct bit_xor : public binary_function<Type, Type, Type> {  
    Type operator()(
    const Type& Left,   
    const Type& Right) const; 
 };  
 
// specialized transparent functor for operator^  
template <>
struct bit_xor<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) ^ std::forward<U>(Right));
};
```  
  
### <a name="parameters"></a>Parámetros  
 `Type`, `T`, `U`  
 Cualquier tipo que admite un `operator^` que toma operandos de los tipos especificados o deducidos.  
  
 `Left`  
 Operando izquierdo de la operación XOR bit a bit. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `T`.  
  
 `Right`  
 Operando derecho de la operación XOR bit a bit. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `U`.  
  
### <a name="return-value"></a>Valor devuelto  
 Resultado de `Left ^ Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator^`.  
  
### <a name="remarks"></a>Comentarios  
 El functor de `bit_xor` está limitado a tipos enteros para los tipos de datos básicos, o a tipos definidos por el usuario que implementan el `operator^` binario.  
  
##  <a name="cref"></a>  cref  
 Construye un `reference_wrapper` const a partir de un argumento.  
  
```  
template <class Ty>  
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>  
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```  
  
### <a name="parameters"></a>Parámetros  
 `Ty`  
 El tipo del argumento que se encapsulará.  
  
 `arg`  
 El argumento que se encapsulará.  
  
### <a name="remarks"></a>Comentarios  
 La primera función devuelve `reference_wrapper<const Ty>(arg.get())`. Úsela para encapsular una referencia const. La segunda función devuelve `reference_wrapper<const Ty>(arg)`. Úsela para volver a encapsular una referencia encapsulada como referencia const.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__functional__cref.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    int i = 1;   
  
    std::cout << "i = " << i << std::endl;   
    std::cout << "cref(i) = " << std::cref(i) << std::endl;   
    std::cout << "cref(neg)(i) = "   
        << std::cref(&neg)(i) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
i = 1  
cref(i) = 1  
cref(neg)(i) = -1  
```  
  
##  <a name="mem_fn"></a>  mem_fn  
 Genera un contenedor de llamadas simple.  
  
```  
template <class Ret, class Ty>  
unspecified mem_fn(Ret Ty::*pm);
```  
  
### <a name="parameters"></a>Parámetros  
 `Ret`  
 Tipo de valor devuelto de la función encapsulada.  
  
 `Ty`  
 El tipo del puntero de función miembro.  
  
### <a name="remarks"></a>Comentarios  
 La función de plantilla devuelve un contenedor simple de llamadas `cw`, con un tipo de resultado débil, de modo que la expresión `cw(t, a2, ..., aN)` es equivalente a `INVOKE(pm, t, a2, ..., aN)`. No produce ninguna excepción.  
  
 El contenedor de llamadas devuelto procede de `std::unary_function<cv Ty*, Ret>` (por tanto, se define el tipo anidado `result_type` como sinónimo de `Ret` y el tipo anidado `argument_type` como sinónimo de `cv Ty*`) solo si el tipo `Ty` es un puntero a una función miembro con el calificador cv `cv` que no toma ningún argumento.  
  
 El contenedor de llamadas devuelto procede de `std::binary_function<cv Ty*, T2, Ret>` (por tanto, se define el tipo anidado `result_type` como sinónimo de `Ret`, el tipo anidado `first argument_type` como sinónimo de `cv Ty*` y el tipo anidado `second argument_type` como sinónimo de `T2`) solo si el tipo `Ty` es un puntero a una función miembro con el calificador cv `cv` que no toma ningún argumento, de tipo `T2`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__functional__mem_fn.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
class Funs   
    {   
public:   
    void square(double x)   
        {   
        std::cout << x << "^2 == " << x * x << std::endl;   
        }   
  
    void product(double x, double y)   
        {   
        std::cout << x << "*" << y << " == " << x * y << std::endl;   
        }   
    };   
  
int main()   
    {   
    Funs funs;   
  
    std::mem_fn(&Funs::square)(funs, 3.0);   
    std::mem_fn(&Funs::product)(funs, 3.0, 2.0);   
  
    return (0);   
    }  
  
```  
  
```Output  
3^2 == 9  
3*2 == 6  
```  
  
##  <a name="mem_fun"></a>  mem_fun  
 Funciones de plantilla auxiliar utilizadas para construir adaptadores de objeto de función para las funciones miembro cuando se inicializan con argumentos de puntero.  
  
```  
template <class Result, class Type>  
mem_fun_t<Result, Type> mem_fun (Result(Type::* pmem)());

template <class Result, class Type, class Arg>  
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg));

template <class Result, class Type>  
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pmem)() const);

template <class Result, class Type, class Arg>  
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg) const);
```  
  
### <a name="parameters"></a>Parámetros  
 `pmem`  
 Un puntero a la función miembro de clase **Type** que se convertirá en un objeto de función.  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto de función **const** o **non_const** de tipo `mem_fun_t` o `mem_fun1_t`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// functional_mem_fun.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
class StoreVals     
{  
    int val;  
public:  
    StoreVals() { val = 0; }  
    StoreVals(int j) { val = j; }  
  
    bool display() { cout << val << " "; return true; }  
    int squareval() { val *= val; return val; }  
    int lessconst(int k) {val -= k; return val; }  
};  
  
int main( )  
{  
    vector<StoreVals *> v1;  
  
    StoreVals sv1(5);  
    v1.push_back(&sv1);  
    StoreVals sv2(10);  
    v1.push_back(&sv2);  
    StoreVals sv3(15);  
    v1.push_back(&sv3);  
    StoreVals sv4(20);  
    v1.push_back(&sv4);  
    StoreVals sv5(25);  
    v1.push_back(&sv5);  
  
    cout << "The original values stored are: " ;  
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));  
    cout << endl;  
  
    // Use of mem_fun calling member function through a pointer  
    // square each value in the vector using squareval ()  
    for_each(v1.begin(), v1.end(), mem_fun<int, StoreVals>(&StoreVals::squareval));     
    cout << "The squared values are: " ;  
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));  
    cout << endl;  
  
    // Use of mem_fun1 calling member function through a pointer  
    // subtract 5 from each value in the vector using lessconst ()  
    for_each(v1.begin(), v1.end(),   
        bind2nd (mem_fun1<int, StoreVals,int>(&StoreVals::lessconst), 5));     
    cout << "The squared values less 5 are: " ;  
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));  
    cout << endl;  
}  
```  
  
##  <a name="mem_fun_ref"></a>  mem_fun_ref  
 Las funciones de plantilla auxiliares usadas para crear adaptadores de objeto de función para las funciones miembro cuando se inicializan con argumentos de referencia.  
  
```  
template <class Result, class Type>  
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pmem)());

template <class Result, class Type, class Arg>  
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pmem)(Arg));

template <class Result, class Type>  
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pmem)() const);

template <class Result, class Type, class Arg>  
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pmem)(Arg) const);
```  
  
### <a name="parameters"></a>Parámetros  
 `pmem`  
 Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto de función `const` o `non_const` de tipo `mem_fun_ref_t` o `mem_fun1_ref_t`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// functional_mem_fun_ref.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
class NumVals  
   {  
   int val;  
   public:  
   NumVals ( ) { val = 0; }  
   NumVals ( int j ) { val = j; }  
  
   bool display ( ) { cout << val << " "; return true; }  
   bool isEven ( ) { return ( bool )  !( val %2 ); }  
   bool isPrime( )  
   {  
      if (val < 2) { return true; }  
      for (int i = 2; i <= val / i; ++i)  
      {  
         if (val % i == 0) { return false; }  
      }  
      return true;  
   }  
};  
  
int main( )  
{  
   vector <NumVals> v1 ( 13 ), v2 ( 13 );  
   vector <NumVals>::iterator v1_Iter, v2_Iter;  
   int i, k;  
  
   for ( i = 0; i < 13; i++ ) v1 [ i ] = NumVals ( i+1 );  
   for ( k = 0; k < 13; k++ ) v2 [ k ] = NumVals ( k+1 );  
  
   cout << "The original values stored in v1 are: " ;  
   for_each( v1.begin( ), v1.end( ),   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
  
   // Use of mem_fun_ref calling member function through a reference  
   // remove the primes in the vector using isPrime ( )  
   v1_Iter = remove_if ( v1.begin( ),  v1.end( ),   
      mem_fun_ref ( &NumVals::isPrime ) );     
   cout << "With the primes removed, the remaining values in v1 are: " ;  
   for_each( v1.begin( ), v1_Iter,   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
  
   cout << "The original values stored in v2 are: " ;  
   for_each( v2.begin( ), v2.end( ),   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
  
   // Use of mem_fun_ref calling member function through a reference  
   // remove the even numbers in the vector v2 using isEven ( )  
   v2_Iter = remove_if ( v2.begin( ),  v2.end( ),   
      mem_fun_ref ( &NumVals::isEven ) );     
   cout << "With the even numbers removed, the remaining values are: " ;  
   for_each( v2.begin( ),  v2_Iter,   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
}  
```  
  
```Output  
The original values stored in v1 are: 1 2 3 4 5 6 7 8 9 10 11 12 13   
With the primes removed, the remaining values in v1 are: 4 6 8 9 10 12   
The original values stored in v2 are: 1 2 3 4 5 6 7 8 9 10 11 12 13   
With the even numbers removed, the remaining values are: 1 3 5 7 9 11 13   
```  
  
##  <a name="not1"></a>  not1  
 Devuelve el complemento de un predicado unario.  
  
```  
template <class UnaryPredicate>  
unary_negate<UnaryPredicate> not1(const UnaryPredicate& pred);
```  
  
### <a name="parameters"></a>Parámetros  
 `pred`  
 Predicado unario que se va a negar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un predicado unario que es la negación del predicado unario modificado.  
  
### <a name="remarks"></a>Comentarios  
 Si una `unary_negate` se construye a partir de un predicado unario **Pred**( *x*), devuelve **!Pred**( *x*).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// functional_not1.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 7; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    vector<int>::iterator::difference_type result1;  
    // Count the elements greater than 10  
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
  
    vector<int>::iterator::difference_type result2;  
    // Use the negator to count the elements less than or equal to 10  
    result2 = count_if(v1.begin(), v1.end(),  
        not1(bind2nd(greater<int>(), 10)));  
  
    cout << "The number of elements in v1 not greater than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
```Output  
The vector v1 = ( 0 5 10 15 20 25 30 35 )  
The number of elements in v1 greater than 10 is: 5.  
The number of elements in v1 not greater than 10 is: 3.  
```  
  
##  <a name="not2"></a>  not2  
 Devuelve el complemento de un predicado binario.  
  
```  
template <class BinaryPredicate>  
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```  
  
### <a name="parameters"></a>Parámetros  
 `func`  
 Predicado binario que se va a negar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un predicado binario que es la negación del predicado binario modificado.  
  
### <a name="remarks"></a>Comentarios  
 Si una `binary_negate` se construye a partir de un predicado binario **BinPred**( *x*, *y*), devuelve ! **BinPred**( *x*, *y*).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// functional_not2.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <cstdlib>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   v1.push_back( 6262 );  
   v1.push_back( 6262 );  
   for ( i = 0 ; i < 5 ; i++ )  
   {  
      v1.push_back( rand( ) );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   // use default binary predicate less<int>( )  
   sort( v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order,   
   // use the binary_negate helper function not2  
   sort( v1.begin( ), v1.end( ), not2(less<int>( ) ) );  
   cout << "Resorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Original vector v1 = ( 6262 6262 41 18467 6334 26500 19169 )  
Sorted vector v1 = ( 41 6262 6262 6334 18467 19169 26500 )  
Resorted vector v1 = ( 26500 19169 18467 6334 6262 6262 41 )  
```  
  
##  <a name="ptr_fun"></a>  ptr_fun  
 Funciones de plantilla auxiliares usadas para convertir punteros de funciones unarias y binarias, respectivamente, en funciones unarias y binarias adaptables.  
  
```  
template <class Arg, class Result>  
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>  
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```  
  
### <a name="parameters"></a>Parámetros  
 `pfunc`  
 El puntero de función unaria o binaria que se convertirá en una función adaptable.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera función de plantilla devuelve la función unaria [pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md) < `Arg`, **Result**>(* `pfunc`).  
  
 La segunda función de plantilla devuelve la función binaria [pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \< **Arg1**, **Arg2**, **Result**>(* `pfunc`).  
  
### <a name="remarks"></a>Comentarios  
 Un puntero de función es un objeto de función y puede pasarse a cualquier algoritmo de la biblioteca estándar de C++ que esté esperando una función como un parámetro, pero no es adaptable. Para usarlo como un adaptador, por ejemplo, al enlazar un valor a este o al usarlo con un negador, debe proporcionarse con los tipos anidados que hacen posible dicha adaptación. La conversión de punteros de función unarios y binarios mediante la función auxiliar `ptr_fun` permite a los adaptadores de función trabajar con punteros de función unarios y binarios.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]  
  
##  <a name="ref"></a>  ref  
 Construye un `reference_wrapper` a partir de un argumento.  
  
```  
template <class Ty>  
reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>  
reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia a `arg`, específicamente, `reference_wrapper<Ty>(arg)`.  
  
### <a name="example"></a>Ejemplo  
  El siguiente ejemplo define dos funciones: una enlazada a una variable de cadena y la otra enlazada a una referencia de la variable de cadena calculada mediante una llamada a `ref`. Cuando el valor de la variable cambia, la primera función continúa usando el valor antiguo y la segunda función usa el nuevo valor.  
  
```cpp  
#include <algorithm>  
#include <functional>  
#include <iostream>  
#include <iterator>  
#include <ostream>  
#include <string>  
#include <vector>  
using namespace std;  
using namespace std;  
using namespace std::placeholders;  
  
bool shorter_than(const string& l, const string& r) {  
    return l.size() < r.size();  
}  
  
int main() {  
    vector<string> v_original;  
    v_original.push_back("tiger");  
    v_original.push_back("cat");  
    v_original.push_back("lion");  
    v_original.push_back("cougar");  
  
    copy(v_original.begin(), v_original.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
  
    string s("meow");  
  
    function<bool (const string&)> f = bind(shorter_than, _1, s);  
    function<bool (const string&)> f_ref = bind(shorter_than, _1, ref(s));  
  
    vector<string> v;  
  
    // Remove elements that are shorter than s ("meow")  
  
    v = v_original;  
    v.erase(remove_if(v.begin(), v.end(), f), v.end());  
  
    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
  
    // Now change the value of s.  
    // f_ref, which is bound to ref(s), will use the  
    // new value, while f is still bound to the old value.  
  
    s = "kitty";  
  
    // Remove elements that are shorter than "meow" (f is bound to old value of s)  
  
    v = v_original;  
    v.erase(remove_if(v.begin(), v.end(), f), v.end());  
  
    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
  
    // Remove elements that are shorter than "kitty" (f_ref is bound to ref(s))  
  
    v = v_original;  
    v.erase(remove_if(v.begin(), v.end(), f_ref), v.end());  
  
    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
}  
```  
  
```Output  
tiger cat lion cougar  
tiger lion cougar  
tiger lion cougar  
tiger cougar  
```  
  
##  <a name="swap"></a>  swap  
 Intercambia dos objetos `function`.  
  
```  
template <class Fty>  
void swap(function<Fty>& f1, function<Fty>& f2);
```  
  
### <a name="parameters"></a>Parámetros  
 `Fty`  
 Tipo controlado por los objetos de función.  
  
 `f1`  
 El primer objeto de función.  
  
 `f2`  
 El segundo objeto de función.  
  
### <a name="remarks"></a>Comentarios  
 La función devuelve `f1.swap(f2)`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__functional__swap.cpp   
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
  
    swap(fn0, fn1);   
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
  
## <a name="see-also"></a>Vea también  
 [\<functional>](../standard-library/functional.md)

