---
title: basic_ios (Clase)
ms.date: 11/04/2016
f1_keywords:
- ios/std::basic_ios
- ios/std::basic_ios::char_type
- ios/std::basic_ios::int_type
- ios/std::basic_ios::off_type
- ios/std::basic_ios::pos_type
- ios/std::basic_ios::traits_type
- ios/std::basic_ios::bad
- ios/std::basic_ios::clear
- ios/std::basic_ios::copyfmt
- ios/std::basic_ios::eof
- ios/std::basic_ios::exceptions
- ios/std::basic_ios::fail
- ios/std::basic_ios::fill
- ios/std::basic_ios::good
- ios/std::basic_ios::imbue
- ios/std::basic_ios::init
- ios/std::basic_ios::move
- ios/std::basic_ios::narrow
- ios/std::basic_ios::rdbuf
- ios/std::basic_ios::rdstate
- ios/std::basic_ios::set_rdbuf
- ios/std::basic_ios::setstate
- ios/std::basic_ios::swap
- ios/std::basic_ios::tie
- ios/std::basic_ios::widen
- ios/std::basic_ios::explicit operator bool
helpviewer_keywords:
- std::basic_ios [C++]
- std::basic_ios [C++], char_type
- std::basic_ios [C++], int_type
- std::basic_ios [C++], off_type
- std::basic_ios [C++], pos_type
- std::basic_ios [C++], traits_type
- std::basic_ios [C++], bad
- std::basic_ios [C++], clear
- std::basic_ios [C++], copyfmt
- std::basic_ios [C++], eof
- std::basic_ios [C++], exceptions
- std::basic_ios [C++], fail
- std::basic_ios [C++], fill
- std::basic_ios [C++], good
- std::basic_ios [C++], imbue
- std::basic_ios [C++], init
- std::basic_ios [C++], move
- std::basic_ios [C++], narrow
- std::basic_ios [C++], rdbuf
- std::basic_ios [C++], rdstate
- std::basic_ios [C++], set_rdbuf
- std::basic_ios [C++], setstate
- std::basic_ios [C++], swap
- std::basic_ios [C++], tie
- std::basic_ios [C++], widen
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
ms.openlocfilehash: c8f883dd4f946c03aaa22dffcf5a3164a539d041
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364920"
---
# <a name="basic_ios-class"></a>basic_ios (Clase)

La plantilla de clase describe las funciones de almacenamiento y miembro comunes a las secuencias de entrada (de la plantilla de clase [basic_istream)](../standard-library/basic-istream-class.md)como a las secuencias de salida (de la plantilla de clase [basic_ostream](../standard-library/basic-ostream-class.md)) que dependen de los parámetros de plantilla. (La clase [ios_base](../standard-library/ios-base-class.md) describe lo que es común y no depende de los parámetros de plantilla.) Un objeto de clase **basic_ios\<clase Elem, clase Traits>** ayuda a controlar una `Traits`secuencia con elementos de tipo `Elem`, cuyos rasgos de carácter están determinados por la clase .

## <a name="syntax"></a>Sintaxis

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Parámetros

*Elem*\
Un tipo.

*Rasgos*\
Una variable de tipo `char_traits`.

## <a name="remarks"></a>Observaciones

Un objeto de clase **basic_ios\<class Elem, class Traits>** almacena:

- Un puntero de enlace a un objeto de tipo [basic_istream](../standard-library/basic-istream-class.md)**\<Elem, Traits>**.

- Un puntero de búfer de secuencia a un objeto de tipo [basic_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, Traits >**.

- [Información de formato](../standard-library/ios-base-class.md).

- [Información de estado de flujo](../standard-library/ios-base-class.md) en un objeto base de tipo [ios_base](../standard-library/ios-base-class.md).

- Un carácter de relleno en un objeto de tipo `char_type`.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_ios](#basic_ios)|Construye la clase `basic_ios`.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Sinónimo del parámetro de plantilla `Elem`.|
|[int_type](#int_type)|Sinónimo de `Traits::int_type`.|
|[off_type](#off_type)|Sinónimo de `Traits::off_type`.|
|[pos_type](#pos_type)|Sinónimo de `Traits::pos_type`.|
|[traits_type](#traits_type)|Sinónimo del parámetro de plantilla `Traits`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Malo](#bad)|Indica una pérdida de integridad del búfer de secuencia.|
|[Claro](#clear)|Borra todas las marcas de error.|
|[copyfmt](#copyfmt)|Copia las marcas de una secuencia a otra.|
|[Ef](#eof)|Indica si se ha alcanzado el extremo de una secuencia.|
|[Excepciones](#exceptions)|Indica qué excepciones iniciará la secuencia.|
|[Fallar](#fail)|Indica un error al extraer un campo válido de una secuencia.|
|[Llenar](#fill)|Especifica o devuelve el carácter que se usará si el texto no tiene el mismo ancho que la secuencia.|
|[bien](#good)|Indica que la secuencia está en buen estado.|
|[imbue](#imbue)|Cambia la configuración regional.|
|[Init](#init)|Llamada por constructores `basic_ios`.|
|[Mover](#move)|Mueve todos los valores, excepto el puntero al búfer de secuencia, desde el parámetro hasta el objeto actual.|
|[narrow](#narrow)|Busca el carácter equivalente a un determinado `char_type`.|
|[rdbuf](#rdbuf)|Redirige la secuencia al búfer especificado.|
|[rdstate](#rdstate)|Lee el estado de bits de las marcas.|
|[set_rdbuf](#set_rdbuf)|Asigna un búfer de secuencia para que sea el búfer de lectura de este objeto de secuencia.|
|[setstate](#setstate)|Establece marcas adicionales.|
|[swap](#swap)|Cambia los valores de este objeto `basic_ios` por los de otro objeto `basic_ios`. No se intercambian los punteros a los búferes de secuencia.|
|[tie](#tie)|Se asegura de que una secuencia se procese antes que otra.|
|[widen](#widen)|Busca el `char_type` equivalente a un determinado carácter.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[explicit operator bool](#op_bool)|Permite el `basic_ios` uso de un objeto como **bool**. La conversión automática de tipo está deshabilitada para evitar efectos secundarios típicos no deseados.|
|[operator void *](#op_void_star)|Indica si la secuencia sigue siendo aceptable.|
|[¡Operador!](#op_not)|Indica si la secuencia no es inaceptable.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<ios>

**Espacio de nombres:** std

## <a name="basic_iosbad"></a><a name="bad"></a>basic_ios::malo

Indica una pérdida de integridad del búfer de flujo.

```cpp
bool bad() const;
```

### <a name="return-value"></a>Valor devuelto

**true** `rdstate & badbit` si es distinto de cero; de lo contrario **falso**.

Para más información sobre `badbit`, vea [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_bad.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.bad( );
    cout << boolalpha;
    cout << b << endl;

    b = cout.good( );
    cout << b << endl;
}
```

## <a name="basic_iosbasic_ios"></a><a name="basic_ios"></a>basic_ios::basic_ios

Construye la clase basic_ios.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Parámetros

*Sb*\
Búfer estándar para almacenar elementos de entrada o salida.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa sus objetos miembro al llamar a [init](#init)(_ *Sb*). El segundo constructor (protegido) deja sus objetos miembro sin inicializar. Una llamada `init` posterior debe inicializar el objeto antes de que se pueda destruir de forma segura.

## <a name="basic_ioschar_type"></a><a name="char_type"></a>basic_ios::char_type

Sinónimo del parámetro de plantilla `Elem`.

```cpp
typedef Elem char_type;
```

## <a name="basic_iosclear"></a><a name="clear"></a>basic_ios::claro

Borra todas las marcas de error.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>Parámetros

*Estado*\
(Opcional) Las marcas que desea establecer después de borrar todas las marcas. Su valor predeterminado es `goodbit`.

*Resubida*\
(Opcional) Especifica si se debe volver a generar la excepción. El valor predeterminado es **false** (no volverá a generar la excepción).

### <a name="remarks"></a>Observaciones

Las banderas `failbit` `eofbit`son `goodbit` `badbit`, , , y . Prueba de estas marcas con [good](#good), [bad](#bad), [eof](#eof) y [fail](#fail)

La función miembro reemplaza la información de estado de la secuencia almacenada por:

`state` &#124; `(`[rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)

Si `state` **&** [las excepciones](#exceptions) son distintas de cero, produce un objeto de [error](../standard-library/ios-base-class.md#failure)de clase .

### <a name="example"></a>Ejemplo

Consulte [rdstate](#rdstate) y [getline](../standard-library/string-functions.md#getline) `clear`para ver ejemplos de uso de .

## <a name="basic_ioscopyfmt"></a><a name="copyfmt"></a>basic_ios::copyfmt

Copia las marcas de una secuencia a otra.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Flujo cuyas marcas se quieren copiar.

### <a name="return-value"></a>Valor devuelto

Objeto **this** del flujo en el que se están copiando las marcas.

### <a name="remarks"></a>Observaciones

La función miembro notifica el **evento de borrado\_** del evento de devolución de llamada . A continuación, copia desde ** \*la** *derecha* en este carácter de relleno, el puntero de empate y la información de formato. Antes de modificar la máscara de `copyfmt_event`excepción, notifica el evento de devolución de llamada . Si, una vez que la copia está completa, **state &**[exceptions](#exceptions) es distinto de cero, la función llama realmente a [clear](#clear) con el argumento [rdstate](#rdstate). Devuelve ** \*este**archivo .

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_copyfmt.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream x( "test.txt" );
    int i = 10;

    x << showpos;
    cout << i << endl;
    cout.copyfmt( x );
    cout << i << endl;
}
```

## <a name="basic_ioseof"></a><a name="eof"></a>basic_ios::eof

Indica si se ha alcanzado el extremo de una secuencia.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si se ha alcanzado el final de la secuencia, **false** en caso contrario.

### <a name="remarks"></a>Observaciones

La función miembro devuelve **true** si [rdstate](#rdstate) `& eofbit` es distinto de cero. Para más información sobre `eofbit`, vea [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_eof.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

int main( int argc, char* argv[] )
{
    fstream   fs;
    int n = 1;
    fs.open( "basic_ios_eof.txt" );   // an empty file
    cout << boolalpha
    cout << fs.eof() << endl;
    fs >> n;   // Read the char in the file
    cout << fs.eof() << endl;
}
```

## <a name="basic_iosexceptions"></a><a name="exceptions"></a>basic_ios::excepciones

Indica qué excepciones iniciará la secuencia.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Parámetros

*Newexcept*\
Marcas que quiere que inicie una excepción.

### <a name="return-value"></a>Valor devuelto

Marcas especificadas actualmente para iniciar una excepción para el flujo.

### <a name="remarks"></a>Observaciones

La primera función miembro devuelve la máscara de excepción almacenada. La segunda función miembro almacena *_Except* en la máscara de excepción y devuelve su anterior valor almacenado. Tenga en cuenta que, al almacenar una nueva máscara de excepción, se puede iniciar una excepción como la llamada a [clear](#clear)([rdstate](#rdstate)).

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_exceptions.cpp
// compile with: /EHsc /GR
#include <iostream>

int main( )
{
    using namespace std;

    cout << cout.exceptions( ) << endl;
    cout.exceptions( ios::eofbit );
    cout << cout.exceptions( ) << endl;
    try
    {
        cout.clear( ios::eofbit );   // Force eofbit on
    }
    catch ( exception &e )
    {
        cout.clear( );
        cout << "Caught the exception." << endl;
        cout << "Exception class: " << typeid(e).name()  << endl;
        cout << "Exception description: " << e.what() << endl;
    }
}
```

```Output
0
1
Caught the exception.
Exception class: class std::ios_base::failure
Exception description: ios_base::eofbit set
```

## <a name="basic_iosfail"></a><a name="fail"></a>basic_ios::fallo

Indica un error al extraer un campo válido de una secuencia.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si [rdstate](#rdstate) `& (badbit|failbit)` es distinto de cero, de lo contrario **false**.

Para más información sobre `failbit`, vea [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_fail.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.fail( );
    cout << boolalpha;
    cout << b << endl;
}
```

## <a name="basic_iosfill"></a><a name="fill"></a>basic_ios::relleno

Especifica o devuelve el carácter que se usará si el texto no tiene el mismo ancho que la secuencia.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Parámetros

*Char*\
Carácter que se quiere como carácter de relleno.

### <a name="return-value"></a>Valor devuelto

Carácter de relleno actual.

### <a name="remarks"></a>Observaciones

La primera función miembro devuelve el carácter de relleno almacenado. La segunda función miembro almacena *Char* en el carácter de relleno y devuelve su valor almacenado anterior.

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_fill.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( )
{
    using namespace std;

    cout << setw( 5 ) << 'a' << endl;
    cout.fill( 'x' );
    cout << setw( 5 ) << 'a' << endl;
    cout << cout.fill( ) << endl;
}
```

```Output
a
xxxxa
x
```

## <a name="basic_iosgood"></a><a name="good"></a>basic_ios::bueno

Indica que la secuencia está en buen estado.

```cpp
bool good() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si [rdstate](#rdstate) `== goodbit` (no se establecen marcas de estado), de lo contrario, **false**.

Para más información sobre `goodbit`, vea [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Ejemplo

Vea [basic_ios::bad](#bad) para obtener un ejemplo de uso de `good`.

## <a name="basic_iosimbue"></a><a name="imbue"></a>basic_ios::imbue

Cambia la configuración regional.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>Parámetros

*Loc*\
Cadena de configuración regional.

### <a name="return-value"></a>Valor devuelto

Configuración regional anterior.

### <a name="remarks"></a>Observaciones

Si [rdbuf](#rdbuf) no es un puntero nulo, la función miembro llama a

`rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)

En cualquier caso, devuelve [ios_base::imbue](../standard-library/ios-base-class.md#imbue)(_ *Loc*).

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_imbue.cpp
// compile with: /EHsc
#include <iostream>
#include <locale>

int main( )
{
    using namespace std;

    cout.imbue( locale( "french_france" ) );
    double x = 1234567.123456;
    cout << x << endl;
}
```

## <a name="basic_iosinit"></a><a name="init"></a>basic_ios::init

Lo llaman los constructores basic_ios.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Parámetros

*_Sb*\
Búfer estándar para almacenar elementos de entrada o salida.

*_Isstd*\
Especifica si se trata de un flujo estándar.

### <a name="remarks"></a>Observaciones

La función miembro almacena valores en todos los objetos miembro, de modo que:

- [rdbuf](#rdbuf) devuelve *_Sb*.

- [tie](#tie) devuelve un puntero nulo.

- [rdstate](#rdstate) devuelve [goodbit](../standard-library/ios-base-class.md#iostate) si *_Sb* es distinto de cero; de lo contrario, devuelve [badbit](../standard-library/ios-base-class.md#iostate).

- [excepciones](#exceptions) `goodbit`devuelve .

- [flags](../standard-library/ios-base-class.md#flags) devuelve [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags).

- [width](../standard-library/ios-base-class.md#width) devuelve 0.

- [precision](../standard-library/ios-base-class.md#precision) devuelve 6.

- [fill](#fill) devuelve el carácter de espacio.

- [getloc](../standard-library/ios-base-class.md#getloc) devuelve `locale::classic`.

- [iword](../standard-library/ios-base-class.md#iword) devuelve cero y [pword](../standard-library/ios-base-class.md#pword) devuelve un puntero nulo para todos los valores de argumento.

## <a name="basic_iosint_type"></a><a name="int_type"></a>basic_ios::int_type

Sinónimo de `traits_type::int_type`.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_iosmove"></a><a name="move"></a>basic_ios::mover

Mueve todos los valores, excepto el puntero al búfer de secuencia, desde el parámetro hasta el objeto actual.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Objeto `ios_base` cuyos valores se van a mover.

### <a name="remarks"></a>Observaciones

La función miembro protegida mueve todos `*this` los `stream buffer pointer`valores almacenados en *right* a excepto el `*this`almacenado , que no cambia a la *derecha* y se establece en un puntero nulo en . El `tie pointer` almacenado se establece en un puntero nulo en *la derecha*.

## <a name="basic_iosnarrow"></a><a name="narrow"></a>basic_ios::estrecho

Busca el carácter equivalente a un determinado `char_type`.

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Parámetros

*Char*\
El **char** para convertir.

*Predeterminado*\
El **char** que desea devolver si no se encuentra ningún equivalente.

### <a name="return-value"></a>Valor devuelto

El **char** equivalente `char_type`a un archivo .

### <a name="remarks"></a>Observaciones

La función [use_facet](../standard-library/basic-filebuf-class.md#open)\<miembro\<devuelve use_facet ctype E> >( [getloc](../standard-library/ios-base-class.md#getloc)( ) ). `narrow`( `Char`, `Default`).

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_narrow.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    wchar_t *x = L"test";
    char y[10];
    cout << x[0] << endl;
    wcout << x << endl;
    y[0] = wcout.narrow( x[0] );
    cout << y[0] << endl;
}
```

## <a name="basic_iosoff_type"></a><a name="off_type"></a>basic_ios::off_type

Sinónimo de `traits_type::off_type`.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_iosoperator-void-"></a><a name="op_void_star"></a>basic_ios::operador void *

Indica si la secuencia sigue siendo aceptable.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Valor devuelto

El operador devuelve un puntero nulo solo si [fail](#fail).

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_opgood.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << (bool)(&cout != 0) << endl;   // Stream is still good
}
```

```Output
1
```

## <a name="basic_iosoperator"></a><a name="op_not"></a>basic_ios::operador!

Indica si la secuencia no es inaceptable.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve [fail](#fail).

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_opbad.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << !cout << endl;   // Stream is not bad
}
```

```Output
0
```

## <a name="basic_iosoperator-bool"></a><a name="op_bool"></a>basic_ios::operador bool

Permite el `basic_ios` uso de un objeto como **bool**. La conversión automática de tipo está deshabilitada para evitar efectos secundarios típicos no deseados.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Observaciones

El operador devuelve un **false** valor `fail()`convertible a false solo si . El tipo de valor devuelto es `void *` convertible solo a **bool**, no a u otro tipo escalar conocido.

## <a name="basic_iospos_type"></a><a name="pos_type"></a>basic_ios::pos_type

Sinónimo de `traits_type::pos_type`.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_iosrdbuf"></a><a name="rdbuf"></a>basic_ios::rdbuf

Redirige la secuencia al búfer especificado.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>Parámetros

*_Sb*\
Flujo.

### <a name="remarks"></a>Observaciones

La primera función miembro devuelve el puntero del búfer de flujo almacenado.

La segunda función miembro almacena *_Sb* en el puntero de búfer de secuencia almacenado y devuelve el valor almacenado anteriormente.

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_rdbuf.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream file( "rdbuf.txt" );
    streambuf *x = cout.rdbuf( file.rdbuf( ) );
    cout << "test" << endl;   // Goes to file
    cout.rdbuf(x);
    cout << "test2" << endl;
}
```

```Output
test2
```

## <a name="basic_iosrdstate"></a><a name="rdstate"></a>basic_ios::rdstate

Lee el estado de bits de las marcas.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>Valor devuelto

Información de estado del flujo almacenado.

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_rdstate.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>
using namespace std;

void TestFlags( ios& x )
{
    cout << ( x.rdstate( ) & ios::badbit ) << endl;
    cout << ( x.rdstate( ) & ios::failbit ) << endl;
    cout << ( x.rdstate( ) & ios::eofbit ) << endl;
    cout << endl;
}

int main( )
{
    fstream x( "c:\test.txt", ios::out );
    x.clear( );
    TestFlags( x );
    x.clear( ios::badbit | ios::failbit | ios::eofbit );
    TestFlags( x );
}
```

```Output
0
0
0

4
2
1
```

## <a name="basic_iossetstate"></a><a name="setstate"></a>basic_ios::setstate

Establece marcas adicionales.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>Parámetros

*_State*\
Marcas adicionales que se van a establecer.

### <a name="remarks"></a>Observaciones

La función miembro llama realmente a [clear](#clear)(_ *State* &#124; [rdstate](#rdstate)).

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_setstate.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
using namespace std;

int main( )
{
    bool b = cout.bad( );
    cout << b << endl;   // Good
    cout.clear( ios::badbit );
    b = cout.bad( );
    // cout.clear( );
    cout << b << endl;   // Is bad, good
    b = cout.fail( );
    cout << b << endl;   // Not failed
    cout.setstate( ios::failbit );
    b = cout.fail( );
    cout.clear( );
    cout << b << endl;   // Is failed, good
    return 0;
}
```

```Output
0
1
```

## <a name="basic_iosset_rdbuf"></a><a name="set_rdbuf"></a>basic_ios::set_rdbuf

Asigna un búfer de secuencia para que sea el búfer de lectura de este objeto de secuencia.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Parámetros

*strbuf*\
Búfer de flujo que se va a convertir en el búfer de lectura.

### <a name="remarks"></a>Observaciones

La función miembro protegida almacena `stream buffer pointer` *strbuf* en el archivo . No llama `clear`a .

## <a name="basic_iostie"></a><a name="tie"></a>basic_ios::empate

Se asegura de que una secuencia se procese antes que otra.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Parámetros

*Str*\
Flujo.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve el puntero de valor equivalente almacenado. La segunda función miembro almacena *str* en el puntero de enlace y devuelve su valor almacenado anterior.

### <a name="remarks"></a>Observaciones

`tie` provoca la sincronización de dos flujos, de modo que las operaciones de un flujo se producen una vez finalizadas las operaciones del otro.

### <a name="example"></a>Ejemplo

En este ejemplo, al unir cin y cout, se garantiza que la cadena "Escriba un número:" pase a la consola antes de que el propio número se extraiga de cin. Esto elimina la posibilidad de que la cadena "Escriba un número:" siga estando en el búfer al leer el número, de modo que se asegure que el usuario realmente tiene algún mensaje al que deba responder. De forma predeterminada, cin y cout están unidos.

```cpp
#include <ios>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    cin.tie( &cout );
    cout << "Enter a number:";
    cin >> i;
}
```

## <a name="basic_iostraits_type"></a><a name="traits_type"></a>basic_ios::traits_type

Sinónimo del parámetro de plantilla `Traits`.

```cpp
typedef Traits traits_type;
```

## <a name="basic_ioswiden"></a><a name="widen"></a>basic_ios::ampliar

Encuentra el `char_type` equivalente a un **char**determinado .

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Parámetros

*Char*\
Carácter que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Encuentra el `char_type` equivalente a un **char**determinado .

### <a name="remarks"></a>Observaciones

La función miembro devuelve [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **E**> >( [getloc](../standard-library/ios-base-class.md#getloc)). `widen`( `Char`).

### <a name="example"></a>Ejemplo

```cpp
// basic_ios_widen.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    char *z = "Hello";
    wchar_t y[2] = {0,0};
    cout << z[0] << endl;
    y[0] = wcout.widen( z[0] );
    wcout << &y[0] << endl;
}
```

## <a name="basic_iosswap"></a><a name="swap"></a>basic_ios::swap

Cambia los valores de este objeto `basic_ios` por los de otro objeto `basic_ios`. Pero no se intercambian los punteros a los búferes de flujo.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Objeto `basic_ios` que se usa para intercambiar valores.

### <a name="remarks"></a>Observaciones

La función miembro protegida intercambia todos `*this` los `stream buffer pointer`valores almacenados *correctamente* con excepto el almacenado .

## <a name="see-also"></a>Consulte también

[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
