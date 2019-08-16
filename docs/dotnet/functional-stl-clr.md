---
title: functional (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/functional>
- cliext::binary_delegate
- cliext::binary_delegate_noreturn
- cliext::binary_negate
- cliext::bind1st
- cliext::bind2nd
- cliext::binder1st
- cliext::binder2nd
- cliext::divides
- cliext::equal_to
- cliext::greater
- cliext::greater_equal
- cliext::less
- cliext::less_equal
- cliext::logical_and
- cliext::logical_not
- cliext::logical_or
- cliext::minus
- cliext::modulus
- cliext::multiplies
- cliext::negate
- cliext::not_equal_to
- cliext::not1
- cliext::not2
- cliext::plus
- cliext::unary_delegate
- cliext::unary_delegate_noreturn
- cliext::unary_negate
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
- binary_delegate function [STL/CLR]
- binary_delegate_noreturn function [STL/CLR]
- binary_negate function [STL/CLR]
- bind1st function [STL/CLR]
- bind2nd function [STL/CLR]
- binder1st function [STL/CLR]
- binder2nd function [STL/CLR]
- divides function [STL/CLR]
- equal_to function [STL/CLR]
- greater function [STL/CLR]
- greater_equal function [STL/CLR]
- less function [STL/CLR]
- less_equal function [STL/CLR]
- logical_and function [STL/CLR]
- logical_not function [STL/CLR]
- logical_or function [STL/CLR]
- minus function [STL/CLR]
- modulus function [STL/CLR]
- multiplies function [STL/CLR]
- negate function [STL/CLR]
- not_equal_to function [STL/CLR]
- not1 function [STL/CLR]
- not2 function [STL/CLR]
- plus function [STL/CLR]
- unary_delegate function [STL/CLR]
- unary_delegate_noreturn function [STL/CLR]
- unary_negate function [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
ms.openlocfilehash: f4a99ea972c6d2ea9b9721664cc75dec257fd7b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393758"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)

Incluya el encabezado STL/CLR `<cliext/functional>` para definir el un número de clases de plantilla y funciones y los delegados de plantilla relacionadas.

## <a name="syntax"></a>Sintaxis

```
#include <functional>
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext/functional >

**Namespace:** cliext

## <a name="declarations"></a>Declaraciones

|delegado|Descripción|
|--------------|-----------------|
|[binary_delegate (STL/CLR)](#binary_delegate)|Delegado de dos argumentos.|
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|Delegado de dos argumentos devuelve **void**.|
|[unary_delegate (STL/CLR)](#unary_delegate)|Un argumento de delegado.|
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|Delegado de un argumento devuelve **void**.|

|Clase|Descripción|
|-----------|-----------------|
|[binary_negate (STL/CLR)](#binary_negate)|Functor para negar un functor de dos argumentos.|
|[binder1st (STL/CLR)](#binder1st)|Functor para enlazar el primer argumento a un functor de dos argumentos.|
|[binder2nd (STL/CLR)](#binder2nd)|Functor para enlazar el segundo argumento a un functor de dos argumentos.|
|[divides (STL/CLR)](#divides)|Dividir functor.|
|[equal_to (STL/CLR)](#equal_to)|Functor de comparación de igualdad.|
|[greater (STL/CLR)](#greater)|Functor de comparación mayor.|
|[greater_equal (STL/CLR)](#greater_equal)|Functor de comparación mayor o igual.|
|[less (STL/CLR)](#less)|Menos functor de comparación.|
|[less_equal (STL/CLR)](#less_equal)|Functor de comparación menor o igual.|
|[logical_and (STL/CLR)](#logical_and)|Functor AND lógico.|
|[logical_not (STL/CLR)](#logical_not)|Lógico no functor.|
|[logical_or (STL/CLR)](#logical_or)|Functor de OR lógico.|
|[minus (STL/CLR)](#minus)|Restar functor.|
|[modulus (STL/CLR)](#modulus)|Functor de módulo.|
|[multiplies (STL/CLR)](#multiplies)|Multiplicar functor.|
|[negate (STL/CLR)](#negate)|Functor para devolver su argumento negada.|
|[not_equal_to (STL/CLR)](#not_equal_to)|Functor de comparación no es igual.|
|[plus (STL/CLR)](#plus)|Agregar functor.|
|[unary_negate (STL/CLR)](#unary_negate)|Functor para negar un functor de un argumento.|

|Función|Descripción|
|--------------|-----------------|
|[bind1st (STL/CLR)](#bind1st)|Genera un binder1st para un argumento y functor.|
|[bind2nd (STL/CLR)](#bind2nd)|Genera un binder2nd para un argumento y functor.|
|[not1 (STL/CLR)](#not1)|Genera un unary_negate para un functor.|
|[not2 (STL/CLR)](#not2)|Genera un binary_negate para un functor.|

## <a name="members"></a>Miembros

## <a name="binary_delegate"></a> binary_delegate (STL/CLR)

La clase genereic describe un delegado de dos argumentos. Usarlo especificar un delegado en cuanto a sus tipos de argumentos y valores devueltos.

### <a name="syntax"></a>Sintaxis

```cpp
generic<typename Arg1,
    typename Arg2,
    typename Result>
    delegate Result binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>Parámetros

*Arg1*<br/>
El tipo del primer argumento.

*Arg2*<br/>
El tipo del segundo argumento.

*Resultado*<br/>
Tipo de valor devuelto.

### <a name="remarks"></a>Comentarios

El delegado genereic describe una función de dos argumentos.

Tenga en cuenta que para:

`binary_delegate<int, int, int> Fun1;`

`binary_delegate<int, int, int> Fun2;`

los tipos de `Fun1` y `Fun2` son sinónimos, mientras que para:

`delegate int Fun1(int, int);`

`delegate int Fun2(int, int);`

no son del mismo tipo.

### <a name="example"></a>Ejemplo

```cpp
// cliext_binary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

bool key_compare(wchar_t left, wchar_t right)
    {
    return (left < right);
    }

typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="binary_delegate_noreturn"></a> binary_delegate_noreturn (STL/CLR)

La clase genereic describe un delegado de dos argumentos que se devuelve **void**. Usarlo especificar un delegado en términos de su argumento.

### <a name="syntax"></a>Sintaxis

```cpp
generic<typename Arg1,
    typename Arg2>
    delegate void binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>Parámetros

*Arg1*<br/>
El tipo del primer argumento.

*Arg2*<br/>
El tipo del segundo argumento.

### <a name="remarks"></a>Comentarios

El delegado genereic describe una función de dos argumentos que devuelve **void**.

Tenga en cuenta que para:

`binary_delegate_noreturn<int, int> Fun1;`

`binary_delegate_noreturn<int, int> Fun2;`

los tipos de `Fun1` y `Fun2` son sinónimos, mientras que para:

`delegate void Fun1(int, int);`

`delegate void Fun2(int, int);`

no son del mismo tipo.

### <a name="example"></a>Ejemplo

```cpp
// cliext_binary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void key_compare(wchar_t left, wchar_t right)
    {
    System::Console::WriteLine("compare({0}, {1}) = {2}",
        left, right, left < right);
    }

typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    kcomp(L'a', L'a');
    kcomp(L'a', L'b');
    kcomp(L'b', L'a');
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(a, a) = False
compare(a, b) = True
compare(b, a) = False
```

## <a name="binary_negate"></a> binary_negate (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el lógicos no de su almacenado functor de dos argumentos. Usarlo especificar un objeto de función en términos de su functor almacenado.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun>
    ref class binary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    explicit binary_negate(Fun% functor);
    binary_negate(binary_negate<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Diversión*<br/>
El tipo del functor almacenado.

## <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|
|stored_function_type|El tipo del functor.|

|Miembro|Descripción|
|------------|-----------------|
|binary_negate|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operator delegate_type^()|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos que se almacena en otro functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve la operación lógica no de la functor almacenado se llama con los dos argumentos.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_binary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="bind1st"></a> bind1st (STL/CLR)

Genera un `binder1st` para un argumento y functor.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun,
    typename Arg>
    binder1st<Fun> bind1st(Fun% functor,
        Arg left);
```

#### <a name="template-parameters"></a>Parámetros de plantilla

*Arg*<br/>
Tipo del argumento.

*Diversión*<br/>
El tipo del functor.

#### <a name="function-parameters"></a>Parámetros de función

*functor*<br/>
Para ajustar el functor.

*left*<br/>
El primer argumento para ajustar.

### <a name="remarks"></a>Comentarios

Devuelve la función de plantilla [binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`. Úselo como una manera cómoda de encapsular un functor de dos argumentos y su primer argumento en un functor de un argumento que lo llame con un segundo argumento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_bind1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="bind2nd"></a> bind2nd (STL/CLR)

Genera un `binder2nd` para un argumento y functor.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun,
    typename Arg>
    binder2nd<Fun> bind2nd(Fun% functor,
        Arg right);
```

#### <a name="template-parameters"></a>Parámetros de plantilla

*Arg*<br/>
Tipo del argumento.

*Diversión*<br/>
El tipo del functor.

#### <a name="function-parameters"></a>Parámetros de función

*functor*<br/>
Para ajustar el functor.

*right*<br/>
El segundo argumento para ajustar.

### <a name="remarks"></a>Comentarios

Devuelve la función de plantilla [binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`. Úselo como una manera cómoda de encapsular un functor de dos argumentos y el segundo argumento en un functor de un argumento que lo llame con un primer argumento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_bind2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="binder1st"></a> binder1st (STL/CLR)

La clase de plantilla describe un functor de un argumento que, cuando se llama, devuelve su almacenado functor de dos argumentos se denomina con su primer argumento almacenado y el segundo argumento proporcionado. Usarlo especificar un objeto de función en términos de su functor almacenado.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun>
    ref class binder1st
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        second_argument_type, result_type>
        delegate_type;

    binder1st(Fun% functor, first_argument_type left);
    binder1st(binder1st<Arg>% right);

    result_type operator()(second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Diversión*<br/>
El tipo del functor almacenado.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|
|stored_function_type|El tipo del functor.|

|Miembro|Descripción|
|------------|-----------------|
|binder1st|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operator delegate_type^()|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de un argumento que almacena un functor de dos argumentos y un primer argumento. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve el resultado de llamar el functor almacenado con el primer argumento almacenado y el segundo argumento proporcionado.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_binder1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="binder2nd"></a> binder2nd (STL/CLR)

La clase de plantilla describe un functor de un argumento que, cuando se llama, devuelve su almacenado functor de dos argumentos que se denomina con el primer argumento proporcionado y el segundo argumento almacenado. Usarlo especificar un objeto de función en términos de su functor almacenado.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun>
    ref class binder2nd
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        first_argument_type, result_type>
        delegate_type;

    binder2nd(Fun% functor, second_argument_type left);
    binder2nd(binder2nd<Arg>% right);

    result_type operator()(first_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Diversión*<br/>
El tipo del functor almacenado.

## <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|
|stored_function_type|El tipo del functor.|

|Miembro|Descripción|
|------------|-----------------|
|binder2nd|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operator delegate_type^()|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de un argumento que almacena un functor de dos argumentos y un segundo argumento. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve el resultado de llamar el functor almacenado con el primer argumento proporcionado y el segundo argumento almacenado.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_binder2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="divides"></a> divide (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el primer argumento dividido por el segundo. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class divides
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    divides();
    divides(divides<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos y el valor devuelto.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|divides|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operator delegate_type^()|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve el primer argumento dividido por el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_divides.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::divides<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 3
```

## <a name="equal_to"></a> equal_to (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento es igual que el segundo. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    equal_to();
    equal_to(equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|equal_to|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operator delegate_type^()|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve true solo si el primer argumento es igual que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="greater"></a> greater (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento es mayor que el segundo. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class greater
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater();
    greater(greater<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|greater|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve true solo si el primer argumento es mayor que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_greater.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
1 0
```

## <a name="greater_equal"></a> greater_equal (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento es mayor o igual que el segundo. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class greater_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater_equal();
    greater_equal(greater_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|greater_equal|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve true solo si el primer argumento es mayor o igual que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_greater_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="less"></a> menor (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento es menor que el segundo. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class less
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less();
    less(less<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|less|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve true solo si el primer argumento es menor que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_less.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="less_equal"></a> less_equal (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento es menor o igual que el segundo. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class less_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less_equal();
    less_equal(less_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|less_equal|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve true solo si el primer argumento es menor o igual que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_less_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
0 1
```

## <a name="logical_and"></a> logical_and (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento y la segunda prueba como true. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class logical_and
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_and();
    logical_and(logical_and<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|logical_and|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve true solo si el primer argumento y la segunda prueba como true.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_logical_and.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 1 0" and " 1 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_and<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
3 0
1 0
```

## <a name="logical_not"></a> logical_not (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si su argumento de prueba como false. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class logical_not
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    logical_not();
    logical_not(logical_not<Arg> %right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|argument_type|El tipo del argumento functor.|
|delegate_type|El tipo del delegado genérico.|
|result_type|El tipo del resultado functor.|

|Miembro|Descripción|
|------------|-----------------|
|logical_not|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de un argumento. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve true solo si su argumento pruebas como false.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_logical_not.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::logical_not<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
0 1
```

## <a name="logical_or"></a> logical_or (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento o las pruebas de segundo como true. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class logical_or
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_or();
    logical_or(logical_or<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|logical_or|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve true solo si el primer argumento o las pruebas de segundo como true.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_logical_or.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(0);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 2 0" and " 0 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_or<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
0 0
1 0
```

## <a name="minus"></a> menos (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el primer argumento menos la segunda. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class minus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    minus();
    minus(minus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos y el valor devuelto.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|minus|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve el primer argumento menos la segunda.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_minus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::minus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 2
```

## <a name="modulus"></a> MODULUS (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el primer argumento de módulo el segundo. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class modulus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    modulus();
    modulus(modulus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos y el valor devuelto.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|modulus|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve el primer argumento de módulo el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_modulus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(2);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 2" and " 3 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::modulus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 2
3 1
1 0
```

## <a name="multiplies"></a> Multiplica (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el primer argumento veces el segundo. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class multiplies
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    multiplies();
    multiplies(multiplies<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos y el valor devuelto.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|multiplies|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve el primer argumento veces el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multiplies.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::multiplies<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
8 3
```

## <a name="negate"></a> negate (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve su argumento negada. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class negate
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    negate();
    negate(negate<Arg>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|argument_type|El tipo del argumento functor.|
|delegate_type|El tipo del delegado genérico.|
|result_type|El tipo del resultado functor.|

|Miembro|Descripción|
|------------|-----------------|
|negate|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de un argumento. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve su argumento negada.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(-3);
    Myvector c3(2, 0);

// display initial contents " 4 -3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::negate<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 -3
-4 3
```

## <a name="not_equal_to"></a> not_equal_to (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento no es igual que el segundo. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class not_equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    not_equal_to();
    not_equal_to(not_equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|not_equal_to|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve true solo si el primer argumento no es igual que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_not_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not_equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="not1"></a> not1 (STL/CLR)

Genera un `unary_negate` para un functor.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun>
    unary_negate<Fun> not1(Fun% functor);
```

#### <a name="template-parameters"></a>Parámetros de plantilla

*Diversión*<br/>
El tipo del functor.

#### <a name="function-parameters"></a>Parámetros de función

*functor*<br/>
Para ajustar el functor.

### <a name="remarks"></a>Comentarios

Devuelve la función de plantilla [unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`. Úselo como una manera cómoda de encapsular un functor de un argumento en un functor que proporciona su operador lógico NOT.

### <a name="example"></a>Ejemplo

```cpp
// cliext_not1.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```

## <a name="not2"></a> not2 (STL/CLR)

Genera un `binary_negate` para un functor.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun>
    binary_negate<Fun> not2(Fun% functor);
```

#### <a name="template-parameters"></a>Parámetros de plantilla

*Diversión*<br/>
El tipo del functor.

#### <a name="function-parameters"></a>Parámetros de función

*functor*<br/>
Para ajustar el functor.

### <a name="remarks"></a>Comentarios

Devuelve la función de plantilla [binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`. Úselo como una manera cómoda de encapsular un functor de dos argumentos en un functor que proporciona su operador lógico NOT.

### <a name="example"></a>Ejemplo

```cpp
// cliext_not2.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="plus"></a> Plus (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el primer argumento y el segundo. Usarlo especificar un objeto de función en términos de su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Arg>
    ref class plus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    plus();
    plus(plus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
El tipo de los argumentos y el valor devuelto.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|El tipo del delegado genérico.|
|first_argument_type|El tipo del primer argumento functor.|
|result_type|El tipo del resultado functor.|
|second_argument_type|El tipo del segundo argumento functor.|

|Miembro|Descripción|
|------------|-----------------|
|plus|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelven el primer argumento y el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_plus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::plus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
6 4
```

## <a name="unary_delegate"></a> unary_delegate (STL/CLR)

La clase genereic describe un delegado de un argumento. Usarlo especificar un delegado en cuanto a sus tipos de argumentos y valores devueltos.

### <a name="syntax"></a>Sintaxis

```cpp
generic<typename Arg,
    typename Result>
    delegate Result unary_delegate(Arg);
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
Tipo del argumento.

*Resultado*<br/>
Tipo de valor devuelto.

### <a name="remarks"></a>Comentarios

El delegado genereic describe una función de un argumento.

Tenga en cuenta que para:

`unary_delegare<int, int> Fun1;`

`unary_delegare<int, int> Fun2;`

los tipos de `Fun1` y `Fun2` son sinónimos, mientras que para:

`delegate int Fun1(int);`

`delegate int Fun2(int);`

no son del mismo tipo.

### <a name="example"></a>Ejemplo

```cpp
// cliext_unary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

int hash_val(wchar_t val)
    {
    return ((val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate<wchar_t, int> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 5
hash(L'b') = 22
```

## <a name="unary_delegate_noreturn"></a> unary_delegate_noreturn (STL/CLR)

La clase genereic describe un delegado de un argumento que devuelva **void**. Usarlo especificar un delegado en cuanto a su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
generic<typename Arg>
    delegate void unary_delegate_noreturn(Arg);
```

#### <a name="parameters"></a>Parámetros

*Arg*<br/>
Tipo del argumento.

### <a name="remarks"></a>Comentarios

El delegado genereic describe una función de un argumento que devuelva **void**.

Tenga en cuenta que para:

`unary_delegare_noreturn<int> Fun1;`

`unary_delegare_noreturn<int> Fun2;`

los tipos de `Fun1` y `Fun2` son sinónimos, mientras que para:

`delegate void Fun1(int);`

`delegate void Fun2(int);`

no son del mismo tipo.

### <a name="example"></a>Ejemplo

```cpp
// cliext_unary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void hash_val(wchar_t val)
    {
    System::Console::WriteLine("hash({0}) = {1}",
       val, (val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate_noreturn<wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    myhash(L'a');
    myhash(L'b');
    return (0);
    }
```

```Output
hash(a) = 5
hash(b) = 22
```

## <a name="unary_negate"></a> unary_negate (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el lógicos no de su almacenado functor de un argumento. Usarlo especificar un objeto de función en términos de su functor almacenado.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun>
    ref class unary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::argument_type argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    unary_negate(Fun% functor);
    unary_negate(unary_negate<Fun>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parámetros

*Diversión*<br/>
El tipo del functor almacenado.

### <a name="member-functions"></a>Funciones miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|argument_type|El tipo del argumento functor.|
|delegate_type|El tipo del delegado genérico.|
|result_type|El tipo del resultado functor.|

|Miembro|Descripción|
|------------|-----------------|
|unary_negate|Construye el functor.|

|Operador|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|delegate_type^|Convierte el functor a un delegado.|

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un functor de un argumento que almacena el functor de un argumento de otra. Define el operador miembro `operator()` que, cuando se llama al objeto como una función, devuelve la operación lógica no de la functor almacenado llamado con el argumento.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_unary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```