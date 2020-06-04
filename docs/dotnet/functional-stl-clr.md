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
ms.openlocfilehash: 2d06a92fea9a702633216e3244879687b66f97d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208733"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)

Incluya el encabezado de STL/CLR `<cliext/functional>` para definir el número de clases de plantilla y los delegados de plantilla y las funciones relacionados.

## <a name="syntax"></a>Sintaxis

```
#include <functional>
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext (/> funcional

**Espacio de nombres:** cliext (

## <a name="declarations"></a>Declaraciones

|Delegar|Descripción|
|--------------|-----------------|
|[binary_delegate (STL/CLR)](#binary_delegate)|Delegado de dos argumentos.|
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|Delegado de dos argumentos que devuelve **void**.|
|[unary_delegate (STL/CLR)](#unary_delegate)|Delegado de un argumento.|
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|Delegado de un argumento que devuelve **void**.|

|Clase|Descripción|
|-----------|-----------------|
|[binary_negate (STL/CLR)](#binary_negate)|Functor para negar un functor de dos argumentos.|
|[binder1st (STL/CLR)](#binder1st)|Functor para enlazar el primer argumento a un functor de dos argumentos.|
|[binder2nd (STL/CLR)](#binder2nd)|Functor para enlazar el segundo argumento a un functor de dos argumentos.|
|[divides (STL/CLR)](#divides)|Dividir functor.|
|[equal_to (STL/CLR)](#equal_to)|Igualar functor.|
|[greater (STL/CLR)](#greater)|Mayor comparación en functor.|
|[greater_equal (STL/CLR)](#greater_equal)|Functor de comparación mayor o igual.|
|[less (STL/CLR)](#less)|Menos funcción de comparación.|
|[less_equal (STL/CLR)](#less_equal)|Functor de comparación menor o igual que.|
|[logical_and (STL/CLR)](#logical_and)|Operador lógico AND functor.|
|[logical_not (STL/CLR)](#logical_not)|NO functor lógico.|
|[logical_or (STL/CLR)](#logical_or)|Lógico o functor.|
|[minus (STL/CLR)](#minus)|Reste functor.|
|[modulus (STL/CLR)](#modulus)|Módulo functor.|
|[multiplies (STL/CLR)](#multiplies)|Funcción de multiplicación.|
|[negate (STL/CLR)](#negate)|Functor para devolver su argumento negado.|
|[not_equal_to (STL/CLR)](#not_equal_to)|No es igual al functor de comparación.|
|[plus (STL/CLR)](#plus)|Agregar functor.|
|[unary_negate (STL/CLR)](#unary_negate)|Functor para negar un funco de un argumento.|

|Función|Descripción|
|--------------|-----------------|
|[bind1st (STL/CLR)](#bind1st)|Genera un binder1st (para un argumento y un functor.|
|[bind2nd (STL/CLR)](#bind2nd)|Genera un binder2nd (para un argumento y un functor.|
|[not1 (STL/CLR)](#not1)|Genera un unary_negate para un functor.|
|[not2 (STL/CLR)](#not2)|Genera un binary_negate para un functor.|

## <a name="members"></a>Members

## <a name="binary_delegate-stlclr"></a><a name="binary_delegate"></a>binary_delegate (STL/CLR)

La clase genereic describe un delegado de dos argumentos. Se usa para especificar un delegado en lo que respecta a sus tipos de argumento y de valor devuelto.

### <a name="syntax"></a>Sintaxis

```cpp
generic<typename Arg1,
    typename Arg2,
    typename Result>
    delegate Result binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>Parámetros

*Arg1*<br/>
Tipo del primer argumento.

*Arg2*<br/>
Tipo del segundo argumento.

*Resultado*<br/>
Tipo de valor devuelto.

### <a name="remarks"></a>Observaciones

El delegado genereic describe una función de dos argumentos.

Tenga en cuenta que para:

`binary_delegate<int, int, int> Fun1;`

`binary_delegate<int, int, int> Fun2;`

los tipos `Fun1` y `Fun2` son sinónimos, mientras que para:

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

## <a name="binary_delegate_noreturn-stlclr"></a><a name="binary_delegate_noreturn"></a>binary_delegate_noreturn (STL/CLR)

La clase genereic describe un delegado de dos argumentos que devuelve **void**. Se usa para especificar un delegado en lo que se refiere a su argumento.

### <a name="syntax"></a>Sintaxis

```cpp
generic<typename Arg1,
    typename Arg2>
    delegate void binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>Parámetros

*Arg1*<br/>
Tipo del primer argumento.

*Arg2*<br/>
Tipo del segundo argumento.

### <a name="remarks"></a>Observaciones

El delegado genereic describe una función de dos argumentos que devuelve **void**.

Tenga en cuenta que para:

`binary_delegate_noreturn<int, int> Fun1;`

`binary_delegate_noreturn<int, int> Fun2;`

los tipos `Fun1` y `Fun2` son sinónimos, mientras que para:

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

## <a name="binary_negate-stlclr"></a><a name="binary_negate"></a>binary_negate (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve NOT lógico de su functor de dos argumentos almacenado. Se usa para especificar un objeto de función en lo que se refiere a su functor almacenada.

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

*Puedes*<br/>
Tipo del functor almacenado.

## <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|
|stored_function_type|Tipo del functor.|

|Member|Descripción|
|------------|-----------------|
|binary_negate|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^ ()|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos que almacena otro functor de dos argumentos. Define el operador miembro `operator()` para que, cuando se llama al objeto como una función, devuelva el elemento lógico NOT del functor almacenado llamado con los dos argumentos.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="bind1st-stlclr"></a><a name="bind1st"></a>bind1st (STL/CLR)

Genera una `binder1st` para un argumento y un functor.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun,
    typename Arg>
    binder1st<Fun> bind1st(Fun% functor,
        Arg left);
```

#### <a name="template-parameters"></a>Parámetros de plantilla

*Argumento*<br/>
Tipo del argumento.

*Puedes*<br/>
Tipo del functor.

#### <a name="function-parameters"></a>Parámetros de función

*functor*<br/>
Functor que se va a ajustar.

*left*<br/>
Primer argumento que se va a ajustar.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [binder1st ((STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`. Se usa como una manera cómoda de encapsular un functor de dos argumentos y su primer argumento en un functor de un argumento que lo llama con un segundo argumento.

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

## <a name="bind2nd-stlclr"></a><a name="bind2nd"></a>bind2nd ((STL/CLR)

Genera una `binder2nd` para un argumento y un functor.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun,
    typename Arg>
    binder2nd<Fun> bind2nd(Fun% functor,
        Arg right);
```

#### <a name="template-parameters"></a>Parámetros de plantilla

*Argumento*<br/>
Tipo del argumento.

*Puedes*<br/>
Tipo del functor.

#### <a name="function-parameters"></a>Parámetros de función

*functor*<br/>
Functor que se va a ajustar.

*right*<br/>
Segundo argumento que se va a ajustar.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [binder2nd ((STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`. Se usa como una manera cómoda de ajustar un functor de dos argumentos y su segundo argumento en un functor de un argumento que lo llama con un primer argumento.

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

## <a name="binder1st-stlclr"></a><a name="binder1st"></a>binder1st ((STL/CLR)

La clase de plantilla describe un funcnte de un argumento que, cuando se llama, devuelve su functor de dos argumentos almacenada llamada con su primer argumento almacenado y el segundo argumento proporcionado. Se usa para especificar un objeto de función en lo que se refiere a su functor almacenada.

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

*Puedes*<br/>
Tipo del functor almacenado.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|
|stored_function_type|Tipo del functor.|

|Member|Descripción|
|------------|-----------------|
|binder1st|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^ ()|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de un argumento que almacena un functor de dos argumentos y un primer argumento. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, devuelve el resultado de llamar al functor almacenado con el primer argumento almacenado y el segundo argumento proporcionado.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="binder2nd-stlclr"></a><a name="binder2nd"></a>binder2nd ((STL/CLR)

La clase de plantilla describe un funcnte de un argumento que, cuando se llama, devuelve su functor de dos argumentos almacenada llamada con el primer argumento proporcionado y su segundo argumento almacenado. Se usa para especificar un objeto de función en lo que se refiere a su functor almacenada.

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

*Puedes*<br/>
Tipo del functor almacenado.

## <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|
|stored_function_type|Tipo del functor.|

|Member|Descripción|
|------------|-----------------|
|binder2nd|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^ ()|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de un argumento que almacena un functor de dos argumentos y un segundo argumento. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, devuelve el resultado de llamar al functor almacenado con el primer argumento y el segundo argumento almacenados.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="divides-stlclr"></a><a name="divides"></a>divisiones (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el primer argumento dividido por el segundo. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
El tipo de los argumentos y el valor devuelto.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|divides|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^ ()|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, devuelve el primer argumento dividido por el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="equal_to-stlclr"></a><a name="equal_to"></a>equal_to (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento es igual que el segundo. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
Tipo de los argumentos.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|equal_to|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^ ()|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, solo devuelve true si el primer argumento es igual que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="greater-stlclr"></a><a name="greater"></a>mayor (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento es mayor que el segundo. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
Tipo de los argumentos.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|greater|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, solo devuelve true si el primer argumento es mayor que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="greater_equal-stlclr"></a><a name="greater_equal"></a>greater_equal (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento es mayor o igual que el segundo. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
Tipo de los argumentos.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|greater_equal|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, solo devuelve true si el primer argumento es mayor o igual que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="less-stlclr"></a><a name="less"></a>Less (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento es menor que el segundo. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
Tipo de los argumentos.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|less|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, solo devuelve true si el primer argumento es menor que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="less_equal-stlclr"></a><a name="less_equal"></a>less_equal (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento es menor o igual que el segundo. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
Tipo de los argumentos.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|less_equal|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, solo devuelve true si el primer argumento es menor o igual que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="logical_and-stlclr"></a><a name="logical_and"></a>logical_and (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento y la segunda prueba son true. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
Tipo de los argumentos.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|logical_and|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, solo devuelve true si el primer argumento y la segunda prueba son true.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="logical_not-stlclr"></a><a name="logical_not"></a>logical_not (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si su argumento se comprueba como false. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
Tipo de los argumentos.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|argument_type|Tipo del argumento functor.|
|delegate_type|Tipo del delegado genérico.|
|result_type|Tipo del resultado del functor.|

|Member|Descripción|
|------------|-----------------|
|logical_not|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de un argumento. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, solo devuelve true si su argumento se comprueba como false.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="logical_or-stlclr"></a><a name="logical_or"></a>logical_or (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento o el segundo comprueba como true. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
Tipo de los argumentos.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|logical_or|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, solo devuelve true si el primer argumento o el segundo se prueban como true.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="minus-stlclr"></a><a name="minus"></a>menos (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el primer argumento menos el segundo. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
El tipo de los argumentos y el valor devuelto.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|menos|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, devuelve el primer argumento menos el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="modulus-stlclr"></a><a name="modulus"></a>módulo (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el primer argumento de módulo en el segundo. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
El tipo de los argumentos y el valor devuelto.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|modulus|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, devuelve el primer argumento módulo en el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="multiplies-stlclr"></a><a name="multiplies"></a>multiplicar (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el primer argumento veces el segundo. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
El tipo de los argumentos y el valor devuelto.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|multiplies|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, devuelve el primer argumento veces el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="negate-stlclr"></a><a name="negate"></a>Negate (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve su argumento negado. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
Tipo de los argumentos.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|argument_type|Tipo del argumento functor.|
|delegate_type|Tipo del delegado genérico.|
|result_type|Tipo del resultado del functor.|

|Member|Descripción|
|------------|-----------------|
|negate|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de un argumento. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, devuelve su argumento negado.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="not_equal_to-stlclr"></a><a name="not_equal_to"></a>not_equal_to (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento no es igual que el segundo. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
Tipo de los argumentos.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|not_equal_to|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, solo devuelve true si el primer argumento no es igual que el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="not1-stlclr"></a><a name="not1"></a>not1 (STL/CLR)

Genera un `unary_negate` para un functor.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun>
    unary_negate<Fun> not1(Fun% functor);
```

#### <a name="template-parameters"></a>Parámetros de plantilla

*Puedes*<br/>
Tipo del functor.

#### <a name="function-parameters"></a>Parámetros de función

*functor*<br/>
Functor que se va a ajustar.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`. Se usa como una manera cómoda de encapsular un functor de un argumento en un functor que entregue su NOT lógico.

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

## <a name="not2-stlclr"></a><a name="not2"></a>not2 (STL/CLR)

Genera un `binary_negate` para un functor.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Fun>
    binary_negate<Fun> not2(Fun% functor);
```

#### <a name="template-parameters"></a>Parámetros de plantilla

*Puedes*<br/>
Tipo del functor.

#### <a name="function-parameters"></a>Parámetros de función

*functor*<br/>
Functor que se va a ajustar.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve [binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`. Se usa como una manera cómoda de encapsular un functor de dos argumentos en un functor que entregue su NOT lógico.

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

## <a name="plus-stlclr"></a><a name="plus"></a>Plus (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el primer argumento más el segundo. Se usa para especificar un objeto de función en lo que se refiere a su tipo de argumento.

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

*Argumento*<br/>
El tipo de los argumentos y el valor devuelto.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|delegate_type|Tipo del delegado genérico.|
|first_argument_type|Tipo del primer argumento de functor.|
|result_type|Tipo del resultado del functor.|
|second_argument_type|Tipo del segundo argumento de functor.|

|Member|Descripción|
|------------|-----------------|
|más|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|operador delegate_type ^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de dos argumentos. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, devuelve el primer argumento más el segundo.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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

## <a name="unary_delegate-stlclr"></a><a name="unary_delegate"></a>unary_delegate (STL/CLR)

La clase genereic describe un delegado de un argumento. Se usa para especificar un delegado en lo que respecta a sus tipos de argumento y de valor devuelto.

### <a name="syntax"></a>Sintaxis

```cpp
generic<typename Arg,
    typename Result>
    delegate Result unary_delegate(Arg);
```

#### <a name="parameters"></a>Parámetros

*Argumento*<br/>
Tipo del argumento.

*Resultado*<br/>
Tipo de valor devuelto.

### <a name="remarks"></a>Observaciones

El delegado genereic describe una función de un solo argumento.

Tenga en cuenta que para:

`unary_delegare<int, int> Fun1;`

`unary_delegare<int, int> Fun2;`

los tipos `Fun1` y `Fun2` son sinónimos, mientras que para:

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

## <a name="unary_delegate_noreturn-stlclr"></a><a name="unary_delegate_noreturn"></a>unary_delegate_noreturn (STL/CLR)

La clase genereic describe un delegado de un argumento que devuelve **void**. Se usa para especificar un delegado en lo que se refiere a su tipo de argumento.

### <a name="syntax"></a>Sintaxis

```cpp
generic<typename Arg>
    delegate void unary_delegate_noreturn(Arg);
```

#### <a name="parameters"></a>Parámetros

*Argumento*<br/>
Tipo del argumento.

### <a name="remarks"></a>Observaciones

El delegado genereic describe una función de un solo argumento que devuelve **void**.

Tenga en cuenta que para:

`unary_delegare_noreturn<int> Fun1;`

`unary_delegare_noreturn<int> Fun2;`

los tipos `Fun1` y `Fun2` son sinónimos, mientras que para:

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

## <a name="unary_negate-stlclr"></a><a name="unary_negate"></a>unary_negate (STL/CLR)

La clase de plantilla describe un functor que, cuando se llama, devuelve el NOT lógico de su functor de un argumento almacenado. Se usa para especificar un objeto de función en lo que se refiere a su functor almacenada.

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

*Puedes*<br/>
Tipo del functor almacenado.

### <a name="member-functions"></a>Funciones de miembro

|Definición de tipo|Descripción|
|---------------------|-----------------|
|argument_type|Tipo del argumento functor.|
|delegate_type|Tipo del delegado genérico.|
|result_type|Tipo del resultado del functor.|

|Member|Descripción|
|------------|-----------------|
|unary_negate|Construye el functor.|

|Operator|Descripción|
|--------------|-----------------|
|operator()|Calcula la función deseada.|
|delegate_type^|Convierte el functor en un delegado.|

### <a name="remarks"></a>Observaciones

La clase de plantilla describe un functor de un argumento que almacena otro funco de un argumento. Define el operador miembro `operator()` de modo que, cuando se llama al objeto como una función, devuelve el elemento lógico NOT del funcnte almacenado llamado con el argumento.

También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirá adecuadamente.

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
