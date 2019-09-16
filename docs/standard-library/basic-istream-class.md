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
ms.openlocfilehash: d1a76e9c639ac56ca693527543ecff5c597456f0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452551"
---
# <a name="basic_istream-class"></a>basic_istream (Clase)

Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo con elementos de tipo `Elem`, también conocido como [char_type](../standard-library/basic-ios-class.md#char_type), cuyos rasgos de caracteres están determinados por la clase *Tr*, también conocida como [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_istream : virtual public basic_ios<Elem, Tr>
```

## <a name="remarks"></a>Comentarios

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

Ambos grupos de funciones llaman a [setstate](../standard-library/basic-ios-class.md#setstate)(`eofbit`) si encuentran el final del archivo al extraer los elementos.

Un objeto de clase `basic_istream`< `Elem`, *Tr*> almacena:

- Un objeto base público virtual de clase [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, *Tr*> `.`

- Recuento de extracción de la última operación de entrada sin formato `count` (llamada en el código anterior).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [basic_ifstream (Clase)](../standard-library/basic-ifstream-class.md) para obtener más información sobre los flujos de entrada.

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[basic_istream](#basic_istream)|Construye un objeto de tipo `basic_istream`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[gcount](#gcount)|Devuelve el número de caracteres leídos durante la última entrada sin formato.|
|[get](#get)|Lee uno o varios caracteres del flujo de entrada.|
|[getline](#getline)|Lee una línea del flujo de entrada.|
|[ignore](#ignore)|Hace que se omita una serie de elementos desde la posición de lectura actual.|
|[peek](#peek)|Devuelve el siguiente carácter que se debe leer.|
|[putback](#putback)|Coloca un carácter especificado en la secuencia.|
|[read](#read)|Lee un número especificado de caracteres de la secuencia y los almacena en una matriz.|
|[readsome](#readsome)|Solo lee del búfer.|
|[seekg](#seekg)|Mueve la posición de lectura de una secuencia.|
|[sentry](#sentry)|La clase anidada describe un objeto cuya declaración estructura las funciones de entrada con y sin formato.|
|[swap](#swap)|Intercambia este objeto `basic_istream` por el parámetro del objeto `basic_istream` proporcionado.|
|[sync](#sync)|Sincroniza el dispositivo de entrada asociado a la secuencia con el búfer de la secuencia.|
|[tellg](#tellg)|Notifica la posición de lectura actual en la secuencia.|
|[unget](#unget)|Devuelve el último carácter leído a la secuencia.|

### <a name="operators"></a>Operadores

|Operador|DESCRIPCIÓN|
|-|-|
|[operator>>](#op_gt_gt)|Llama a una función del flujo de entrada o lee datos con formato del flujo de entrada.|
|[operator=](#op_eq)|Asigna a este objeto el `basic_istream` de la parte derecha del operador. Se trata de una asignación de movimiento con una referencia `rvalue` que no deja ninguna copia.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<istream>

**Espacio de nombres:** std

## <a name="basic_istream"></a>  basic_istream::basic_istream

Construye un objeto de tipo `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parámetros

*strbuf*\
Objeto de tipo [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**true** si se trata de un flujo estándar; en caso contrario, **false**.

*correcta*\
Objeto `basic_istream` que se va a copiar.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa la clase base al llamar a [init](../standard-library/basic-ios-class.md#init)(_S `trbuf`). También almacena cero en el recuento de extracción. Para más información sobre este recuento de extracción, vea la sección Comentarios del tema [basic_istream (Clase)](../standard-library/basic-istream-class.md).

El segundo constructor inicializa la clase base al llamar a `move( right)`. También almacena _R `ight.gcount()` en el recuento de extracción y cero en el recuento de extracción de _R `ight`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) para más información sobre los flujos de entrada.

## <a name="gcount"></a>  basic_istream::gcount

Devuelve el número de caracteres leídos durante la última entrada sin formato.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Valor devuelto

Recuento de extracción.

### <a name="remarks"></a>Comentarios

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

## <a name="get"></a>  basic_istream::get

Lee uno o varios caracteres del flujo de entrada.

```cpp
int_type get();

basic_istream<Elem, Tr>& get(Elem& Ch);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count, Elem Delim);

basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf);
basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf, Elem Delim);
```

### <a name="parameters"></a>Parámetros

*contabiliza*\
Número de caracteres que se van a leer desde `strbuf`.

*DELIM*\
Carácter que debe finalizar la lectura si se encuentra antes del *recuento*.

*CAD*\
Cadena en la que se va a escribir.

*Cam*\
Carácter que se va a obtener.

*strbuf*\
Búfer en el que se va a escribir.

### <a name="return-value"></a>Valor devuelto

El formato sin parámetros de get devuelve el elemento read como un entero o el final del archivo. Los formatos restantes devuelven el flujo (* `this`).

### <a name="remarks"></a>Comentarios

La primera de estas funciones de entrada sin formato extrae un elemento, si es posible, como si devolviera `rdbuf`-> `sbumpc`. De lo contrario, devuelve **traits_type::** [eof](../standard-library/char-traits-struct.md#eof). Si la función no extrae ningún elemento, llama a [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

La segunda función extrae el elemento [int_type](../standard-library/basic-ios-class.md#int_type) `meta` del mismo modo. Si `meta` se compara en relación de igualdad con **traits_type::eof**, la función llama a `setstate`(**failbit**). De lo contrario, almacena **traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)(`meta`) en `Ch`. La función devuelve **\*this**.

La tercera función devuelve **get**(_ *Str*, `count`, `widen`('\ **n**')).

La cuarta función extrae hasta los elementos *Count* -1 y los almacena en la matriz a partir de _ *Str*. Siempre almacena `char_type` después de cualquier elemento extraído que almacene. Para realizar pruebas, la extracción se detiene:

- Al final del archivo.

- Después de que la función extraiga un elemento que compare igual a *DELIM*, en cuyo caso el elemento se devuelve a la secuencia controlada.

- Después de que la función Extraiga los elementos *Count* -1.

Si la función no extrae ningún elemento, llama a `setstate`(**failbit**). En cualquier caso, devuelve **\*this**.

La quinta función devuelve **get**(**strbuf**, `widen`('\ **n**')).

La sexta función extrae los elementos y los inserta `strbuf`en. La extracción se detiene al final del archivo o en un elemento que se compara con relación de igualdad con _ *Delim*, que no se extrae. También se detiene sin extraer el elemento en cuestión si se produce un error en una inserción o si se inicia una excepción (que se detecta pero no vuelve a iniciarse). Si la función no extrae ningún elemento, llama a `setstate`(**failbit**). En cualquier caso, la función devuelve **\*this**.

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

## <a name="getline"></a>  basic_istream::getline

Obtiene una línea del flujo de entrada.

```cpp
basic_istream<Elem, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Elem, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type Delim);
```

### <a name="parameters"></a>Parámetros

*contabiliza*\
Número de caracteres que se van a leer desde `strbuf`.

*DELIM*\
Carácter que debe finalizar la lectura si se encuentra antes del *recuento*.

*CAD*\
Cadena en la que se va a escribir.

### <a name="return-value"></a>Valor devuelto

Flujo ( **\*this**).

### <a name="remarks"></a>Comentarios

La primera de estas funciones de entrada sin formato devuelve **getline**(_ *Str*, `count`, `widen`(' `\`**n**')).

La segunda función extrae hasta los elementos *Count* -1 y los almacena en la matriz a partir de _ *Str*. Siempre almacena el carácter de fin de cadena después de los elementos extraídos que almacena. Para realizar pruebas, la extracción se detiene:

- Al final del archivo.

- Después de que la función extraiga un elemento que compare igual a *DELIM*, en cuyo caso el elemento no se vuelve a colocar ni se anexa a la secuencia controlada.

- Después de que la función Extraiga los elementos *Count* -1.

Si la función no extrae ningún elemento o *recuento* -1, llama a [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). En cualquier caso, devuelve **\*this**.

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

## <a name="ignore"></a>  basic_istream::ignore

Hace que se omita una serie de elementos desde la posición de lectura actual.

```cpp
basic_istream<Elem, Tr>& ignore(
    streamsize count = 1,
    int_type Delim = traits_type::eof());
```

### <a name="parameters"></a>Parámetros

*contabiliza*\
Número de elementos que se van a omitir desde la posición de lectura actual.

*DELIM*\
Elemento que, si se encuentra antes del recuento `ignore` , hace que devuelva y permita que se lean todos los elementos después de *DELIM* .

### <a name="return-value"></a>Valor devuelto

Flujo ( **\*this**).

### <a name="remarks"></a>Comentarios

La función de entrada sin formato extrae los elementos de *recuento* y los descarta. Sin embargo, si *Count* es igual a **numeric_limits\<int >:: Max**, se tomará como arbitrariamente grande. La extracción se detiene temprano en el final del archivo o `Ch` en un elemento de modo que **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `Ch`) se compare con igual que *DELIM* (que también se extrae). La función devuelve **\*this**.

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

## <a name="op_gt_gt"></a>  basic\_istream::operator>>

Llama a una función del flujo de entrada o lee datos con formato del flujo de entrada.

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));
basic_istream& operator>>(basic_streambuf<Elem, Tr>* strbuf);
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

Flujo ( **\*this**).

### <a name="remarks"></a>Comentarios

El \<encabezado IStream > también define varios operadores de extracción globales. Para más información, vea [operator>> (\<istream>)](../standard-library/istream-operators.md#op_gt_gt).

La primera función miembro garantiza que una expresión con el formato **istr** >> `ws` llame a [ws](../standard-library/istream-functions.md#ws)(**istr**) y luego devuelva **\*this**. Las funciones segunda y tercera garantizan que los demás manipuladores, como [hex](../standard-library/ios-functions.md#hex), se comporten de forma similar. Las funciones restantes son las funciones de entrada con formato.

La función:

```cpp
basic_istream& operator>>(
    basic_streambuf<Elem, Tr>* strbuf);
```

extrae los elementos, si _ *Strbuf* no es un puntero nulo y los inserta en *Strbuf*. La extracción se detiene al final del archivo. También se detiene sin extraer el elemento en cuestión si se produce un error en una inserción o si se inicia una excepción (que se detecta pero no vuelve a iniciarse). Si la función no extrae ningún elemento, llama a [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). En cualquier caso, la función devuelve **\*this**.

La función:

```cpp
basic_istream& operator>>(bool& val);
```

extrae un campo y lo convierte en un valor booleano al llamar a [use_facet](../standard-library/basic-filebuf-class.md#open) < `num_get`\< **Elem**, **InIt**>([getloc](../standard-library/ios-base-class.md#getloc)). [get](../standard-library/ios-base-class.md#getloc)(**InIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), `Init`(0), **\*this**, `getloc`, `val`). Aquí, **InIt** se define como [istreambuf_iterator](../standard-library/istreambuf-iterator-class.md) \< **Elem**, **Tr**>. La función devuelve **\*this**.

Las funciones:

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

extraen un campo y lo convierten en un valor numérico al llamar a `use_facet`< `num_get`\< **Elem**, **InIt**>(`getloc`). [get](#get)(**InIt**(`rdbuf`), `Init`(0), **\*this**, `getloc`, `val`). Aquí, **InIt** se define como `istreambuf_iterator` \< **Elem**, **TR**> y `val` tiene el tipo **Long**, **unsigned Long**o **void** <strong>\*</strong> según sea necesario.

Si el valor convertido no se puede representar como el tipo `val`de, la función llama a`failbit` [setstate](../standard-library/basic-ios-class.md#setstate)(). En cualquier caso, la función devuelve **\*this**.

Las funciones:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

extraen un campo y lo convierten en un valor numérico al llamar a `use_facet`< `num_get`\< **Elem**, **InIt**>(`getloc`). **get**(**InIt**(`rdbuf`), `Init`(0), **\*this**, `getloc`, `val`). Aquí, `InIt` se define como `istreambuf_iterator` \< **Elem**, **TR**> y `val` tiene el tipo **Double** o **Long Double** según sea necesario.

Si el valor convertido no se puede representar como el tipo de `val`, la función llama a `setstate`(**failbit**). En cualquier caso, devuelve **\*this**.

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

## <a name="op_eq"></a>  basic_istream::operator=

Asigna a este objeto el `basic_istream` de la parte derecha del operador. Se trata de una asignación de movimiento con una referencia `rvalue` que no deja ninguna copia.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parámetros

*correcta*\
Referencia `rvalue` a un objeto `basic_ifstream`.

### <a name="return-value"></a>Valor devuelto

Devuelve *this.

### <a name="remarks"></a>Comentarios

El operador miembro llama a swap `( right)`.

## <a name="peek"></a>  basic_istream::peek

Devuelve el siguiente carácter que se debe leer.

```cpp
int_type peek();
```

### <a name="return-value"></a>Valor devuelto

Siguiente carácter que se va a leer.

### <a name="remarks"></a>Comentarios

La función de entrada sin formato extrae un elemento, si es posible, como si devolviera `rdbuf` -> [sgetc](../standard-library/basic-streambuf-class.md#sgetc). De lo contrario, devuelve **traits_type::** [eof](../standard-library/char-traits-struct.md#eof).

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

## <a name="putback"></a>  basic_istream::putback

Coloca un carácter especificado en la secuencia.

```cpp
basic_istream<Elem, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Parámetros

*Cam*\
Carácter que se va a volver a colocar en el flujo.

### <a name="return-value"></a>Valor devuelto

Flujo ( **\*this**).

### <a name="remarks"></a>Comentarios

La [función de entrada sin formato](../standard-library/basic-istream-class.md) devuelve *CH*, si es posible, como si se llamara a [rdbuf](../standard-library/basic-ios-class.md#rdbuf)`->`[sputbackc](../standard-library/basic-streambuf-class.md#sputbackc). Si rdbuf es un puntero nulo, o si la llamada a `sputbackc` devuelve **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), la función llama a [setstate](../standard-library/basic-ios-class.md#setstate)(`badbit`). En cualquier caso, devuelve **\*this**.

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

## <a name="read"></a>  basic_istream::read

Lee un número especificado de caracteres de la secuencia y los almacena en una matriz.

Este método es potencialmente inseguro, ya que se basa en el llamador para comprobar que los valores pasados son correctos.

```cpp
basic_istream<Elem, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parámetros

*CAD*\
Matriz en la que se van a leer los caracteres.

*contabiliza*\
Número de caracteres que se va a leer.

### <a name="return-value"></a>Valor devuelto

Flujo (`*this`).

### <a name="remarks"></a>Comentarios

La función de entrada sin formato extrae los elementos de *recuento* y los almacena en la matriz `Str`a partir de _. La extracción se detiene anticipadamente al final del archivo, en cuyo caso la función [llama a setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). En cualquier caso, devuelve `*this`.

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

## <a name="readsome"></a>  basic_istream::readsome

Lee el número especificado de valores de carácter.

Este método es potencialmente inseguro, ya que se basa en el llamador para comprobar que los valores pasados son correctos.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parámetros

*CAD*\
Matriz en la que `readsome` almacena los caracteres que lee.

*contabiliza*\
Número de caracteres que se va a leer.

### <a name="return-value"></a>Valor devuelto

Número de caracteres realmente leídos, [gcount](#gcount).

### <a name="remarks"></a>Comentarios

Esta función de entrada sin formato extrae hasta *contar* los elementos del flujo de entrada y los almacena en la matriz *Str*.

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

## <a name="seekg"></a>  basic_istream::seekg

Mueve la posición de lectura de una secuencia.

```cpp
basic_istream<Elem, Tr>& seekg(pos_type pos);

basic_istream<Elem, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parámetros

*abre*\
Posición absoluta a la que se va a mover el puntero de lectura.

*habilitar*\
Desplazamiento para desplazar el puntero de lectura en relación con la *forma*.

*hacia*\
Una de las enumeraciones [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir).

### <a name="return-value"></a>Valor devuelto

Flujo ( **\*this**).

### <a name="remarks"></a>Comentarios

La primera función miembro realiza una búsqueda absoluta y la segunda una búsqueda relativa.

> [!NOTE]
> No use la segunda función miembro con archivos de texto, ya que el estándar de C++ no admite las búsquedas relativas en archivos de texto.

Si [FAIL](../standard-library/basic-ios-class.md#fail) es false, la primera función miembro llama a **newpos** = [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)( `pos`), para algún `pos_type` objeto `newpos`temporal. Si `fail` es false, la segunda función llama a **newpos** = **rdbuf** -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)( `way` `off`,). En cualquier caso, si ( `off_type`) **newpos** = = ( `off_type`) (-1) (se produce un error en la operación de posicionamiento `istr`), la función llama a. [setstate](../standard-library/basic-ios-class.md#setstate) (`failbit`). Ambas funciones devuelven **\*this**.

Si [fail](../standard-library/basic-ios-class.md#fail) es True, las funciones miembro no hacen nada.

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

## <a name="sentry"></a>  basic_istream::sentry

La clase anidada describe un objeto cuya declaración estructura las funciones de entrada con y sin formato.

clase Sentry {Public: Explicit Sentry (basic_istream\<Elem, tr > & _Istr, bool _Noskip = false); Operator bool () Const;};

### <a name="remarks"></a>Comentarios

Si `_Istr.`[good](../standard-library/basic-ios-class.md#good) es True, el constructor:

- Llama a `_Istr`. [tie](../standard-library/basic-ios-class.md#tie) -> [flush](../standard-library/basic-ostream-class.md#flush) si `_Istr`. `tie` no es un puntero nulo

- Llama realmente a [ws](../standard-library/istream-functions.md#ws)(`_Istr`) si `_Istr`. [flags](../standard-library/ios-base-class.md#flags) **&** [skipws](../standard-library/ios-functions.md#skipws) es distinto de cero

Si, después de dicha de preparación, `_Istr`. `good`es false, el constructor llama `_Istr`a. [setstate](../standard-library/basic-ios-class.md#setstate) (`failbit`). En cualquier caso, el constructor almacena el valor devuelto por `_Istr`. `good`en `status`. Una llamada posterior a `operator bool` proporciona este valor almacenado.

## <a name="swap"></a>  basic_istream::swap

Intercambia el contenido de dos objetos `basic_istream`.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parámetros

*correcta*\
Referencia lvalue a un objeto `basic_istream`.

### <a name="remarks"></a>Comentarios

La función miembro llama a [basic_ios::swap](../standard-library/basic-ios-class.md#swap)`(right)`. También intercambia el recuento de extracción con el recuento de extracción de la *derecha*.

## <a name="sync"></a>  basic_istream::sync

Sincroniza el dispositivo de entrada asociado a la secuencia con el búfer de la secuencia.

```cpp
int sync();
```

### <a name="return-value"></a>Valor devuelto

Si [rdbuf](../standard-library/basic-ios-class.md#rdbuf) es un puntero nulo, la función devuelve -1. De lo contrario, llama a `rdbuf` -> [pubsync](../standard-library/basic-streambuf-class.md#pubsync). Si eso devuelve-1, la función llama a [setstate](../standard-library/basic-ios-class.md#setstate)(`badbit`) y devuelve -1. De lo contrario, la función devuelve cero.

## <a name="tellg"></a>  basic_istream::tellg

Notifica la posición de lectura actual en la secuencia.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Valor devuelto

La posición actual en la secuencia.

### <a name="remarks"></a>Comentarios

Si [fail](../standard-library/basic-ios-class.md#fail) es False, la función miembro devuelve [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **in**). De lo contrario, devuelve `pos_type`(-1).

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

## <a name="unget"></a>  basic_istream::unget

Devuelve el último carácter leído a la secuencia.

```cpp
basic_istream<Elem, Tr>& unget();
```

### <a name="return-value"></a>Valor devuelto

Flujo ( **\*this**).

### <a name="remarks"></a>Comentarios

La [función de entrada sin formato](../standard-library/basic-istream-class.md) vuelve a colocar el elemento anterior en el flujo, si es posible, como si llamara a `rdbuf` -> [sungetc](../standard-library/basic-streambuf-class.md#sungetc). Si [rdbuf](../standard-library/basic-ios-class.md#rdbuf) es un puntero nulo, o si la llamada a `sungetc` devuelve **traits_type::** [EOF](../standard-library/basic-ios-class.md#eof), la función llama a [setstate](../standard-library/basic-ios-class.md#setstate)(`badbit`). En cualquier caso, devuelve **\*this**.

Para más información sobre los errores de `unget`, vea [basic_streambuf::sungetc](../standard-library/basic-streambuf-class.md#sungetc).

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

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
