---
title: basic_istream (Clase)
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_istream
- istream/std::basic_istream::gcount
- istream/std::basic_istream::get
- istream/std::basic_istream::getline
- 'istream/std::basic_istream::'
- istream/std::basic_istream::peek
- istream/std::basic_istream::putback
- istream/std::basic_istream::read
- istream/std::basic_istream::readsome
- istream/std::basic_istream::seekg
- istream/std::basic_istream::sentry
- istream/std::basic_istream::swap
- istream/std::basic_istream::sync
- istream/std::basic_istream::tellg
- istream/std::basic_istream::unget
helpviewer_keywords:
- std::basic_istream [C++]
- std::basic_istream [C++], gcount
- std::basic_istream [C++], get
- std::basic_istream [C++], getline
- std::basic_istream [C++], OVERWRITE
- std::basic_istream [C++], peek
- std::basic_istream [C++], putback
- std::basic_istream [C++], read
- std::basic_istream [C++], readsome
- std::basic_istream [C++], seekg
- std::basic_istream [C++], sentry
- std::basic_istream [C++], swap
- std::basic_istream [C++], sync
- std::basic_istream [C++], tellg
- std::basic_istream [C++], unget
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
ms.openlocfilehash: 03a6e3a65d6dc8c2fa896949855bd23a01578e5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376825"
---
# <a name="basic_istream-class"></a>basic_istream (Clase)

Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo con elementos de tipo `Char_T`, también conocido como [char_type](../standard-library/basic-ios-class.md#char_type), cuyos rasgos de caracteres están determinados por la clase *Tr*, también conocida como [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_istream : virtual public basic_ios<Char_T, Tr>
```

## <a name="remarks"></a>Observaciones

La mayoría de las funciones miembro que sobrecargan [operator>>](#op_gt_gt) son funciones de entrada con formato. Siguen el patrón:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```

Muchas otras funciones miembro son funciones de entrada sin formato. Siguen el patrón:

```cpp
iostate state = goodbit;
count = 0;    // the value returned by gcount
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```

Ambos grupos de [`setstate`](../standard-library/basic-ios-class.md#setstate) `(eofbit)` funciones llaman si encuentran el final del archivo al extraer elementos.

Un objeto `basic_istream<Char_T, Tr>` de clase almacena:

- Un objeto base público [`basic_ios`](../standard-library/basic-ios-class.md) `<Char_T, Tr>`virtual de clase .

- Un recuento de extracción para la `count` última operación de entrada sin formato (llamada en el código anterior).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [basic_ifstream (Clase)](../standard-library/basic-ifstream-class.md) para obtener más información sobre los flujos de entrada.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_istream](#basic_istream)|Construye un objeto de tipo `basic_istream`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[gcount](#gcount)|Devuelve el número de caracteres leídos durante la última entrada sin formato.|
|[get](#get)|Lee uno o varios caracteres del flujo de entrada.|
|[getline](#getline)|Lee una línea del flujo de entrada.|
|[Ignorar](#ignore)|Hace que se omita una serie de elementos desde la posición de lectura actual.|
|[Peek](#peek)|Devuelve el siguiente carácter que se debe leer.|
|[putback](#putback)|Coloca un carácter especificado en la secuencia.|
|[Leer](#read)|Lee un número especificado de caracteres de la secuencia y los almacena en una matriz.|
|[readsome](#readsome)|Solo lee del búfer.|
|[seekg](#seekg)|Mueve la posición de lectura de una secuencia.|
|[sentry](#sentry)|La clase anidada describe un objeto cuya declaración estructura las funciones de entrada con y sin formato.|
|[swap](#swap)|Intercambia este objeto `basic_istream` por el parámetro del objeto `basic_istream` proporcionado.|
|[Sincronizar](#sync)|Sincroniza el dispositivo de entrada asociado de la secuencia con el búfer de la secuencia.|
|[tellg](#tellg)|Notifica la posición de lectura actual en la secuencia.|
|[unget](#unget)|Devuelve el último carácter leído a la secuencia.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador>>](#op_gt_gt)|Llama a una función del flujo de entrada o lee datos con formato del flujo de entrada.|
|[operador](#op_eq)|Asigna a este objeto el `basic_istream` de la parte derecha del operador. Es una asignación de `rvalue` movimiento que implica una referencia que no deja una copia atrás.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<istream>

**Espacio de nombres:** std

## <a name="basic_istreambasic_istream"></a><a name="basic_istream"></a>basic_istream::basic_istream

Construye un objeto de tipo `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parámetros

*strbuf*\
Objeto de tipo [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**true** si es una secuencia estándar; de lo contrario, **false**.

*Correcto*\
Objeto `basic_istream` que se va a copiar.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa la [`init`](../standard-library/basic-ios-class.md#init) `(strbuf)`clase base llamando a . También almacena cero en el recuento de extracción. Para obtener más información acerca de este recuento de extracción, consulte la sección Comentarios de la información general [de basic_istream clase.](../standard-library/basic-istream-class.md)

El segundo constructor inicializa la clase base al llamar a `move(right)`. También almacena `right.gcount()` en el recuento de extracción y almacena cero en el recuento de extracción para *right**.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) para más información sobre los flujos de entrada.

## <a name="basic_istreamgcount"></a><a name="gcount"></a>basic_istream::gcount

Devuelve el número de caracteres leídos durante la última entrada sin formato.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Valor devuelto

Recuento de extracción.

### <a name="remarks"></a>Observaciones

Use [basic_istream::get](#get) para leer caracteres sin formato.

### <a name="example"></a>Ejemplo

```cpp
// basic_istream_gcount.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   cout << "Type the letter 'a': ";

   ws( cin );
   char c[10];

   cin.get( &c[0],9 );
   cout << c << endl;

   cout << cin.gcount( ) << endl;
}
```

```Input
a
```

```Output
Type the letter 'a': a
1
```

## <a name="basic_istreamget"></a><a name="get"></a>basic_istream::get

Lee uno o varios caracteres del flujo de entrada.

```cpp
int_type get();

basic_istream<Char_T, Tr>& get(Char_T& Ch);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count, Char_T delimiter);

basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf);
basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf, Char_T delimiter);
```

### <a name="parameters"></a>Parámetros

*Contar*\
Número de caracteres que se van a leer desde *strbuf*.

*Delimitador*\
El carácter que debe terminar la lectura si se encuentra antes de *contar*.

*Str*\
Cadena en la que se va a escribir.

*Ch*\
Carácter que se va a obtener.

*strbuf*\
Búfer en el que se va a escribir.

### <a name="return-value"></a>Valor devuelto

El formato sin parámetros de get devuelve el elemento read como un entero o el final del archivo. Los formatos restantes devuelven el flujo (* `this`).

### <a name="remarks"></a>Observaciones

La primera función de entrada sin formato extrae un `rdbuf->sbumpc`elemento, si es posible, como si se devolviera . De lo `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)contrario, devuelve . Si la función no extrae ningún elemento, llama a [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`.

La segunda función extrae el elemento [int_type](../standard-library/basic-ios-class.md#int_type)`meta` del mismo modo. Si `meta` se compara `traits_type::eof`igual a `setstate(failbit)`, la función llama a . De lo `traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(meta)` contrario, almacena en *Ch*. La función devuelve __*this__.

La tercera `get(str, count, widen('\n'))`función devuelve .

La cuarta función `count - 1` extrae hasta los elementos y los almacena en la matriz a partir de *str*. Siempre almacena `char_type` después de cualquier elemento extraído que almacene. Para realizar pruebas, la extracción se detiene:

- Al final del archivo.

- Después de que la función extraiga un elemento que se compara igual al *delimitador*. En este caso, el elemento se vuelve a colocar en la secuencia controlada.

- Después de `count - 1` que la función extraiga elementos.

Si la función no extrae ningún elemento, llama a `setstate(failbit)`. En cualquier caso, devuelve __*this__.

La quinta `get(strbuf, widen('\n'))`función devuelve .

La sexta función extrae los elementos y los inserta en *strbuf*. La extracción se detiene al final del archivo o en un elemento que se compara igual que el *delimitador,* que no se extrae. También se detiene sin extraer el elemento en cuestión si se produce un error en una inserción o si se inicia una excepción (que se detecta pero no vuelve a iniciarse). Si la función no extrae ningún elemento, llama a `setstate(failbit)`. En cualquier caso, la función devuelve __*this__.

### <a name="example"></a>Ejemplo

```cpp
// basic_istream_get.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   c[0] = cin.get( );
   cin.get( c[1] );
   cin.get( &c[2],3 );
   cin.get( &c[4], 4, '7' );

   cout << c << endl;
}
```

```Output
1111
```

## <a name="basic_istreamgetline"></a><a name="getline"></a>basic_istream::getline

Obtiene una línea del flujo de entrada.

```cpp
basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type delimiter);
```

### <a name="parameters"></a>Parámetros

*Contar*\
Número de caracteres que se van a leer desde *strbuf*.

*Delimitador*\
El carácter que debe terminar la lectura si se encuentra antes de *contar*.

*Str*\
Cadena en la que se va a escribir.

### <a name="return-value"></a>Valor devuelto

La secuencia (__*this__).

### <a name="remarks"></a>Observaciones

La primera de estas funciones `getline(str, count, widen('\n'))`de entrada sin formato devuelve .

La segunda función `count - 1` extrae hasta los elementos y los almacena en la matriz a partir de *str*. Siempre almacena el carácter de fin de cadena después de los elementos extraídos que almacena. Para realizar pruebas, la extracción se detiene:

- Al final del archivo.

- Después de que la función extraiga un elemento que se compara igual al *delimitador*. En este caso, el elemento no se vuelve a colocar y no se anexa a la secuencia controlada.

- Después de `count - 1` que la función extraiga elementos.

Si la función no `count - 1` extrae [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`ningún elemento o elemento, llama a . En cualquier caso, devuelve __*this__.

### <a name="example"></a>Ejemplo

```cpp
// basic_istream_getline.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   cin.getline( &c[0], 5, '2' );
   cout << c << endl;
}
```

```Output
121
```

## <a name="basic_istreamignore"></a><a name="ignore"></a>basic_istream::ignorar

Hace que se omita una serie de elementos desde la posición de lectura actual.

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>Parámetros

*Contar*\
Número de elementos que se van a omitir desde la posición de lectura actual.

*Delimitador*\
Elemento que, si se encuentra `ignore` antes del recuento, hace que se devuelva y permita que se lean todos los elementos después *del delimitador.*

### <a name="return-value"></a>Valor devuelto

La secuencia (__*this__).

### <a name="remarks"></a>Observaciones

La función de entrada sin formato extrae hasta para *contar* elementos y los descarta. Si *count* `numeric_limits<int>::max`es igual a , sin embargo, se toma como arbitrariamente grande. La extracción se detiene al `Ch` principio `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(Ch)` del final del archivo o de un elemento que se compara igual al *delimitador* (que también se extrae). La función devuelve __*this__.

### <a name="example"></a>Ejemplo

```cpp
// basic_istream_ignore.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   char chararray[10];
   cout << "Type 'abcdef': ";
   cin.ignore( 5, 'c' );
   cin >> chararray;
   cout << chararray;
}
```

```Output
Type 'abcdef': abcdef
def
```

## <a name="basic_istreamoperator"></a><a name="op_gt_gt"></a>istream básico::operador\_>>

Llama a una función del flujo de entrada o lee datos con formato del flujo de entrada.

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Char_T, Tr>& (* Pfn)(basic_ios<Char_T, Tr>&));
basic_istream& operator>>(basic_streambuf<Char_T, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

### <a name="parameters"></a>Parámetros

*Pfn*\
Puntero de función.

*strbuf*\
Objeto de tipo `stream_buf`.

*Val*\
Valor que se va a leer desde el flujo.

### <a name="return-value"></a>Valor devuelto

La secuencia (__*this__).

### <a name="remarks"></a>Observaciones

El \<encabezado istream> también define varios operadores de extracción globales. Para más información, vea [operator>> (\<istream>)](../standard-library/istream-operators.md#op_gt_gt).

La primera función miembro garantiza `istr >> ws` que [`ws`](../standard-library/istream-functions.md#ws) `(istr)`una expresión del formulario llama a y, a continuación, devuelve __*this__. La segunda y tercera funciones garantizan que [`hex`](../standard-library/ios-functions.md#hex)otros manipuladores, como , se comporten de forma similar. Las funciones restantes son las funciones de entrada formateadas.

La función:

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

extrae elementos, si *strbuf* no es un puntero nulo, y los inserta en *strbuf*. La extracción se detiene al final del archivo. También se detiene sin extraer el elemento en cuestión si se produce un error en una inserción o si se inicia una excepción (que se detecta pero no vuelve a iniciarse). Si la función no extrae ningún elemento, llama a [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`. En cualquier caso, la función devuelve __*this__.

La función:

```cpp
basic_istream& operator>>(bool& val);
```

extrae un campo y lo convierte en [`use_facet`](../standard-library/basic-filebuf-class.md#open) `< num_get<Char_T, InIt>(` [`getloc`](../standard-library/ios-base-class.md#getloc) `).` [`get`](../standard-library/ios-base-class.md#getloc) `( InIt(` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)un valor booleano llamando a `), Init(0), *this, getloc, val)`. Aquí, `InIt` se [`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md) `<Char_T, Tr>`define como . La función devuelve __*this__.

Cada una de las funciones:

```cpp
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
```

extraer un campo y convertirlo en `use_facet<num_get<Char_T, InIt>(getloc).` [`get`](#get) `(InIt(rdbuf), Init(0), *this, getloc, val)`un valor numérico llamando a . Aquí, `InIt` se `istreambuf_iterator<Char_T, Tr>`define como , y *val* tiene el tipo **long**, **unsigned long**o **void** <strong>\*</strong> según sea necesario.

Si el valor convertido no se puede representar como el [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`tipo de *val*, la función llama . En cualquier caso, la función devuelve __*this__.

Cada una de las funciones:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

extraer un campo y convertirlo en `use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)`un valor numérico llamando a . Aquí, `InIt` se `istreambuf_iterator<Char_T, Tr>`define como , y *val* tiene el tipo **double** o **long double** según sea necesario.

Si el valor convertido no se puede *val*representar como el `setstate(failbit)`tipo de val , la función llama . En cualquier caso, devuelve __*this__.

### <a name="example"></a>Ejemplo

```cpp
// istream_basic_istream_op_is.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)
{
   if ( i == cin )
   {
      cerr << "i is cin" << endl;
   }
   return i;
}

int main( )
{
   int i = 0;
   cin >> somefunc;
   cin >> i;
   cout << i << endl;
   cin >> hex2;
   cin >> i;
   cout << i << endl;
}
```

## <a name="basic_istreamoperator"></a><a name="op_eq"></a>basic_istream::operador ?

Asigna a este objeto el `basic_istream` de la parte derecha del operador. Es una asignación de `rvalue` movimiento que implica una referencia que no deja una copia atrás.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Referencia `rvalue` a un objeto `basic_ifstream`.

### <a name="return-value"></a>Valor devuelto

Devuelve __*this__.

### <a name="remarks"></a>Observaciones

El operador `swap(right)`miembro llama a .

## <a name="basic_istreampeek"></a><a name="peek"></a>basic_istream::peek

Devuelve el siguiente carácter que se debe leer.

```cpp
int_type peek();
```

### <a name="return-value"></a>Valor devuelto

Siguiente carácter que se va a leer.

### <a name="remarks"></a>Observaciones

La función de entrada sin formato extrae un `rdbuf->` [`sgetc`](../standard-library/basic-streambuf-class.md#sgetc)elemento, si es posible, como si se devolviera . De lo `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)contrario, devuelve .

### <a name="example"></a>Ejemplo

```cpp
// basic_istream_peek.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;
   cout << "Type 'abcde': ";

   c2 = cin.peek( );
   cin.getline( &c[0], 9 );

   cout << c2 << " " << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
a abcde
```

## <a name="basic_istreamputback"></a><a name="putback"></a>basic_istream::putback

Coloca un carácter especificado en la secuencia.

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Parámetros

*Ch*\
Carácter que se va a volver a colocar en el flujo.

### <a name="return-value"></a>Valor devuelto

La secuencia (__*this__).

### <a name="remarks"></a>Observaciones

La función de [entrada sin formato](../standard-library/basic-istream-class.md) devuelve *Ch* [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc), si es posible, como si llamara a . Si `rdbuf` es un puntero nulo, `sputbackc` o `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)si la [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)`llamada a devuelve , la función llama a . En cualquier caso, devuelve __*this__.

### <a name="example"></a>Ejemplo

```cpp
// basic_istream_putback.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2, c3;

   c2 = cin.get( );
   c3 = cin.get( );
   cin.putback( c2 );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Output
qwq
```

## <a name="basic_istreamread"></a><a name="read"></a>basic_istream::leer

Lee un número especificado de caracteres de la secuencia y los almacena en una matriz.

Este método es potencialmente inseguro, ya que se basa en el llamador para comprobar que los valores pasados son correctos.

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parámetros

*Str*\
Matriz en la que se van a leer los caracteres.

*Contar*\
Número de caracteres que se va a leer.

### <a name="return-value"></a>Valor devuelto

Flujo (`*this`).

### <a name="remarks"></a>Observaciones

La función de entrada sin formato extrae hasta para *contar* elementos y los almacena en la matriz a partir *de str*. La extracción se detiene al principio [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`del final del archivo, en cuyo caso la función llama . En cualquier caso, devuelve __*this__.

### <a name="example"></a>Ejemplo

```cpp
// basic_istream_read.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
    char c[10];
    int count = 5;

    cout << "Type 'abcde': ";

    // Note: cin::read is potentially unsafe, consider
    // using cin::_Read_s instead.
    cin.read(&c[0], count);
    c[count] = 0;

    cout << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
abcde
```

## <a name="basic_istreamreadsome"></a><a name="readsome"></a>basic_istream::readsome

Lee el número especificado de valores de carácter.

Este método es potencialmente inseguro, ya que se basa en el llamador para comprobar que los valores pasados son correctos.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parámetros

*Str*\
Matriz en la que `readsome` almacena los caracteres que lee.

*Contar*\
Número de caracteres que se va a leer.

### <a name="return-value"></a>Valor devuelto

El número de caracteres realmente leídos, [`gcount`](#gcount).

### <a name="remarks"></a>Observaciones

Esta función de entrada sin formato extrae *hasta* contar elementos de la secuencia de entrada y los almacena en la matriz *str*.

Esta función no espera a la entrada. Lee aquellos datos que estén disponibles.

### <a name="example"></a>Ejemplo

```cpp
// basic_istream_readsome.cpp
// compile with: /EHsc /W3
#include <iostream>
using namespace std;

int main( )
{
   char c[10];
   int count = 5;

   cout << "Type 'abcdefgh': ";

   // cin.read blocks until user types input.
   // Note: cin::read is potentially unsafe, consider
   // using cin::_Read_s instead.
   cin.read(&c[0], 2);

   // Note: cin::readsome is potentially unsafe, consider
   // using cin::_Readsome_s instead.
   int n = cin.readsome(&c[0], count);  // C4996
   c[n] = 0;
   cout << n << " characters read" << endl;
   cout << c << endl;
}
```

## <a name="basic_istreamseekg"></a><a name="seekg"></a>basic_istream::seekg

Mueve la posición de lectura de una secuencia.

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parámetros

*Pos*\
Posición absoluta a la que se va a mover el puntero de lectura.

*fuera*\
Un desplazamiento para mover el puntero de lectura en relación con *el camino*.

*sentido*\
Una de las enumeraciones [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir).

### <a name="return-value"></a>Valor devuelto

La secuencia (__*this__).

### <a name="remarks"></a>Observaciones

La primera función miembro realiza una búsqueda absoluta y la segunda una búsqueda relativa.

> [!NOTE]
> No use la segunda función miembro con archivos de texto, ya que el estándar de C++ no admite las búsquedas relativas en archivos de texto.

Si [`fail`](../standard-library/basic-ios-class.md#fail) es false, la `newpos =` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) `(pos)`primera función miembro llama a , para algún `pos_type` objeto `newpos`temporal . Si `fail` es false, la `newpos = rdbuf->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `( off, way)`segunda función llama a . En cualquier caso, `(off_type)newpos == (off_type)(-1)` si (se produce un `istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`error en la operación de posicionamiento), la función llama a . Ambas funciones devuelven __*this__.

Si [`fail`](../standard-library/basic-ios-class.md#fail) es true, las funciones miembro no hacen nada.

### <a name="example"></a>Ejemplo

```cpp
// basic_istream_seekg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
   using namespace std;
   ifstream file;
   char c, c1;

   file.open( "basic_istream_seekg.txt" );
   file.seekg(2);   // seek to position 2
   file >> c;
   cout << c << endl;
}
```

## <a name="basic_istreamsentry"></a><a name="sentry"></a>basic_istream::centinela

La clase anidada describe un objeto cuya declaración estructura las funciones de entrada con y sin formato.

```cpp
class sentry {
   public:
   explicit sentry(
      basic_istream<Char_T, Tr>& _Istr,
      bool _Noskip = false);
   operator bool() const;
   };
```

### <a name="remarks"></a>Observaciones

Si `_Istr.` [`good`](../standard-library/basic-ios-class.md#good) es true, el constructor:

- Llama `_Istr.` [`tie`](../standard-library/basic-ios-class.md#tie) `->` [`flush`](../standard-library/basic-ostream-class.md#flush) `_Istr.tie` a if no es un puntero nulo.

- Efectivamente [`ws`](../standard-library/istream-functions.md#ws) `(_Istr)` llama `_Istr.` [`flags`](../standard-library/ios-base-class.md#flags) `&` [`skipws`](../standard-library/ios-functions.md#skipws) si es distinto de cero.

Si después de `_Istr.good` alguna de estas `_Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`preparaciones, es false, el constructor llama a . En cualquier caso, el constructor `_Istr.good` almacena `status`el valor devuelto por en . Una llamada `operator bool` posterior para entregar este valor almacenado.

## <a name="basic_istreamswap"></a><a name="swap"></a>basic_istream::swap

Intercambia el contenido de dos objetos `basic_istream`.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Referencia lvalue a un objeto `basic_istream`.

### <a name="remarks"></a>Observaciones

La función [`basic_ios::swap`](../standard-library/basic-ios-class.md#swap) `(right)`miembro llama a . También intercambia el recuento de extracción con el recuento de extracción para *el derecho*.

## <a name="basic_istreamsync"></a><a name="sync"></a>basic_istream::sincronización

Sincroniza el dispositivo de entrada asociado de la secuencia con el búfer de la secuencia.

```cpp
int sync();
```

### <a name="return-value"></a>Valor devuelto

Si [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) es un puntero nulo, la función devuelve -1. De lo `rdbuf->` [`pubsync`](../standard-library/basic-streambuf-class.md#pubsync)contrario, llama a . Si esa llamada devuelve -1, la función llama [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` y devuelve -1. De lo contrario, la función devuelve cero.

## <a name="basic_istreamtellg"></a><a name="tellg"></a>basic_istream::tellg

Notifica la posición de lectura actual en la secuencia.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Valor devuelto

La posición actual en la secuencia.

### <a name="remarks"></a>Observaciones

Si [`fail`](../standard-library/basic-ios-class.md#fail) es false, la [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `(0, cur, in)`función miembro devuelve . En caso contrario, devuelve `pos_type(-1)`.

### <a name="example"></a>Ejemplo

```cpp
// basic_istream_tellg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;
    ifstream file;
    char c;
    streamoff i;

    file.open("basic_istream_tellg.txt");
    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;

    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;
}
```

## <a name="basic_istreamunget"></a><a name="unget"></a>basic_istream::desenconseguir

Devuelve el último carácter leído a la secuencia.

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>Valor devuelto

La secuencia (__*this__).

### <a name="remarks"></a>Observaciones

La función de [entrada sin formato](../standard-library/basic-istream-class.md) devuelve el elemento anterior en `rdbuf->` [`sungetc`](../standard-library/basic-streambuf-class.md#sungetc)la secuencia, si es posible, como si llamara a . Si [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) es un puntero nulo, `sungetc` o `traits_type::` [`eof`](../standard-library/basic-ios-class.md#eof)si la [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)`llamada a devuelve , la función llama a . En cualquier caso, devuelve __*this__.

Para obtener `unget` información sobre [`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc)cómo se puede producir un error, consulte .

### <a name="example"></a>Ejemplo

```cpp
// basic_istream_unget.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;

   cout << "Type 'abc': ";
   c2 = cin.get( );
   cin.unget( );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Input
abc
```

```Output
Type 'abc': abc
abc
```

## <a name="see-also"></a>Consulte también

[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
