---
title: Clase integer_sequence | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
dev_langs:
- C++
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 90fe4e380072d85e19cf2c4ecb1d9e3e4b913842
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="integersequence-class"></a>Clase integer_sequence
Representa una secuencia de enteros. Puede usarse para deducir y expandir paquetes de parámetros en tipos de variádicos como std::tuple\<T...> que se pasan como argumentos a una función.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <class T, T... Vals>  
struct integer_sequence  
```  
  
#### <a name="parameters"></a>Parámetros  
 T  
 Tipo de los valores; debe ser un tipo integral: bool, char, char16_t, char32_t, wchar_t o tipos enteros con o sin signo.  
  
 Vals  
 Paquete de parámetros sin tipo que representa una secuencia de valores de tipo entero T.  
  
## <a name="members"></a>Miembros  
  
|||  
|-|-|  
|`static size_t size() noexcept`|Número de elementos de la secuencia.|  
|typedef T value_type|Tipo de cada elemento de la secuencia. Debe ser un tipo entero.|  
  
## <a name="remarks"></a>Comentarios  
 Los paquetes de parámetros que se pasan directamente a una función pueden desempaquetarse sin aplicaciones auxiliares de biblioteca especiales. Cuando un paquete de parámetros forma parte de un tipo que se pasa a una función y se necesitan índices para acceder a los elementos, la manera más fácil de descomprimirlo es usar `integer_sequence` y sus alias de tipo relacionados `make_integer_sequence`, `index_sequence`, `make_index_sequence` y `index_sequence_for`.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo se basa en la propuesta original [N3658](http://open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html). Muestra cómo usar `integer_sequence` para crear `std::tuple` a partir de `std::array<T,N>` y cómo usar `integer_sequence` para llegar a los miembros de la tupla.  
  
 En la función `a2t`, `index_sequence` es un alias de `integer_sequence` según el tipo entero `size_t`. `make_index_sequence` es un alias que, en tiempo de compilación, crea `index_sequence` de base cero con el mismo número de elementos que la matriz que el llamador pasa. `a2t` pasa `index_sequence` por valor a `a2t_`, donde la expresión `a[I]...` desempaqueta `I` y, a continuación, los elementos se suministran a `make_tuple`, que los consume como argumentos individuales. Por ejemplo, si la secuencia contiene tres elementos, se llama a `make_tuple` como make_tuple(a[0], a[1], a[2]). Los elementos de matriz pueden ser cualquier tipo.  
  
 La función apply acepta [std::tuple](../standard-library/tuple-class.md) y genera integer_sequence mediante la clase auxiliar `tuple_size`. Tenga en cuenta que [std::decay_t](../standard-library/decay-class.md)_ es necesario porque [tuple_size](../standard-library/tuple-size-class-tuple.md) no funciona con tipos de referencia. La función `apply_` desempaqueta los miembros de la tupla y los reenvía como argumentos independientes a una llamada de función. En este ejemplo, la función es una expresión lambda sencilla que imprime los valores.  
  
```  
  
#include <stddef.h>  
#include <iostream>  
#include <tuple>  
#include <utility>  
#include <array>  
#include <string>  
  
using namespace std;  
  
// Create a tuple from the array and the index_sequence  
template<typename Array, size_t... I>  
auto a2t_(const Array& a, index_sequence<I...>)  
{  
    return make_tuple(a[I]...);  
}  
  
// Create an index sequence for the array, and pass it to the  
// implementation function a2t_  
template<typename T, size_t N>  
auto a2t(const array<T, N>& a)  
{  
    return a2t_(a, make_index_sequence<N>());  
}  
  
// Call function F with the tuple members as separate arguments.   
template<typename F, typename Tuple = tuple<T...>, size_t... I>  
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)   
{  
    return forward<F>(f)(get<I>(forward<Tuple>(args))...);  
}  
  
// Create an index_sequence for the tuple, and pass it with the   
// function object and the tuple to the implementation function apply_  
template<typename F, typename Tuple = tuple<T...>>  
decltype(auto) apply(F&& f, Tuple&& args)  
{  
    using Indices = make_index_sequence<tuple_size<decay_t<Tuple>>::value >;  
    return apply_(forward<F>(f), forward<Tuple>(args), Indices());  
}  
  
int main()  
{   
    const array<string, 3> arr { "Hello", "from", "C++14" };  
  
    //Create a tuple given a array  
    auto tup = a2t(arr);   
  
    // Extract the tuple elements  
    apply([](const string& a, const string& b, const string& c) {cout << a << " " << b << " " << c << endl; }, tup);  
  
    char c;  
    cin >> c;  
}  
  
```  
  
  Para realizar `index_sequence` para un paquete de parámetros, use `index_sequence_for`\<T...>, que es un alias para `make_index_sequence`\<sizeof...(T)>.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: <type_traits>  
  
 Espacio de nombres: std  
  
## <a name="see-also"></a>Vea también  
 [Puntos suspensivos y plantillas variádicas](../cpp/ellipses-and-variadic-templates.md)

