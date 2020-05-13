---
title: basic_ostream (Clase)
ms.date: 03/27/2019
f1_keywords:
- ostream/std::basic_ostream
- ostream/std::basic_ostream::flush
- ostream/std::basic_ostream::put
- ostream/std::basic_ostream::seekp
- ostream/std::basic_ostream::sentry
- ostream/std::basic_ostream::swap
- ostream/std::basic_ostream::tellp
- ostream/std::basic_ostream::write
helpviewer_keywords:
- std::basic_ostream [C++]
- std::basic_ostream [C++], flush
- std::basic_ostream [C++], put
- std::basic_ostream [C++], seekp
- std::basic_ostream [C++], sentry
- std::basic_ostream [C++], swap
- std::basic_ostream [C++], tellp
- std::basic_ostream [C++], write
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
ms.openlocfilehash: e074eb30d31c316411dd43f9a7a019defb64e9fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376761"
---
# <a name="basic_ostream-class"></a>basic_ostream (Clase)

Esta plantilla de clase describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de secuencia con elementos de tipo `Elem`, también conocido como [char_type](../standard-library/basic-ios-class.md#char_type), cuyos rasgos de carácter están determinados por la clase `Tr`, también conocida como [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

*Elem*\
`char_type`.

*Tr*\
El carácter `traits_type`.

## <a name="remarks"></a>Observaciones

La mayoría de las funciones miembro que sobrecargan [operator<<](#basic_ostream_operator_lt_lt) son funciones de salida con formato. Siguen el patrón:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{try
{<convert and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
width(0);
// Except for operator<<(Elem)
setstate(state);

return (*this);
```

Otras dos funciones miembro son funciones de salida sin formato. Siguen el patrón:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (!ok)
    state |= badbit;
else
{try
{<obtain and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
setstate(state);

return (*this);
```

Ambos grupos de funciones llaman a [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**) si encuentran un error al insertar elementos.

Un objeto de clase basic_istream\< **Elem**, **Tr**> solo almacena un objeto base público virtual de clase [basic_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr>**.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [basic_ofstream (Clase)](../standard-library/basic-ofstream-class.md) para obtener más información sobre los flujos de salida.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_ostream](#basic_ostream)|Construye un objeto `basic_ostream`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[rubor](#flush)|Vacía el búfer.|
|[put](#put)|Coloca un carácter en una secuencia.|
|[seekp](#seekp)|Restablece la posición en el flujo de salida.|
|[sentry](#sentry)|La clase anidada describe un objeto cuya declaración estructura las funciones de salida con y sin formato.|
|[swap](#swap)|Cambia los valores de este objeto `basic_ostream` por los del objeto `basic_ostream` proporcionado.|
|[tellp](#tellp)|Notifica la posición en el flujo de salida.|
|[Escribir](#write)|Coloca los caracteres en una secuencia.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador](#op_eq)|Asigna el valor del parámetro de objeto `basic_ostream` a este objeto.|
|[operador<<](#basic_ostream_operator_lt_lt)|Escribe en la secuencia.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<ostream>

**Espacio de nombres:** std

## <a name="basic_ostreambasic_ostream"></a><a name="basic_ostream"></a>basic_ostream::basic_ostream

Construye un objeto `basic_ostream`.

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>Parámetros

*strbuf*\
Objeto de tipo [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**true** si se trata de una secuencia estándar; de lo contrario, **false**.

*Correcto*\
Referencia a un valor R a un objeto de tipo `basic_ostream`.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa la clase base`strbuf`llamando a [init](../standard-library/basic-ios-class.md#init)( ). El segundo constructor inicializa la clase base llamando a [basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) para obtener más información sobre los flujos de salida.

## <a name="basic_ostreamflush"></a><a name="flush"></a>basic_ostream::flush

Vacía el búfer.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Valor devuelto

Referencia al objeto basic_ostream.

### <a name="remarks"></a>Observaciones

Si [rdbuf](../standard-library/basic-ios-class.md#rdbuf) no es un puntero nulo, la función llama a **rdbuf->**[pubsync](../standard-library/basic-streambuf-class.md#pubsync). Si eso devuelve -1, la función llama a [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**). Devuelve ** \*este**archivo .

### <a name="example"></a>Ejemplo

```cpp
// basic_ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "test";
   cout.flush();
}
```

```Output
test
```

## <a name="basic_ostreamoperatorltlt"></a><a name="basic_ostream_operator_lt_lt"></a>basic_ostream::operador&lt;&lt;

Escribe en la secuencia.

```cpp
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

### <a name="parameters"></a>Parámetros

*Pfn*\
Puntero de función.

*strbuf*\
Puntero a un objeto `stream_buf` .

*Val*\
Elemento que se va a escribir en el flujo.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto basic_ostream.

### <a name="remarks"></a>Observaciones

El \<encabezado de> ostream también define varios operadores de inserción global. Para obtener más información, consulte [operador<<](../standard-library/ostream-operators.md#op_lt_lt).

La primera función miembro garantiza `ostr << endl` que una expresión del formulario llama a [endl](../standard-library/ostream-functions.md#endl)**(ostr)** y, a continuación, devuelve ** \*este**. Las funciones segunda y tercera garantizan que los demás manipuladores, como [hex](../standard-library/ios-functions.md#hex), se comporten de forma similar. Las funciones restantes son todas funciones de salida con formato.

La función

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

extrae elementos de *strbuf*, si *strbuf* no es un puntero nulo y los inserta. La extracción se detiene al final del archivo o si una extracción inicia una excepción (que se vuelve a iniciar). También se detiene, sin extraer el elemento en cuestión, si se produce un error en una inserción. Si la función no inserta ningún elemento, o si una extracción inicia una excepción, la función llama a [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). En cualquier caso, ** \*** la función devuelve este archivo .

La función

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

convierte `_Val` a un campo booleano y lo inserta llamando a [use_facet](../standard-library/basic-filebuf-class.md#open) **<num_put\<Elem, OutIt>** `(` [getloc](../standard-library/ios-base-class.md#getloc)). [put](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), **\*this**, `getloc`, **val**). Aquí, `OutIt` se define como [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem, Tr>**. La función devuelve ** \*este**archivo .

Funciones

```cpp
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

cada uno convierte *val* en un campo numérico e insértelo llamando a **use_facet<num_put\<Elem, OutIt>**(`getloc`). **poner**(**OutIt**`rdbuf`( `getloc`), ** \*esto**, , **val**). Aquí, **OutIt** se define como **ostreambuf_iterator\<Elem, Tr>**. La función devuelve ** \*este**archivo .

Funciones

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

cada uno convierte *val* en un campo numérico e insértelo llamando a use_facet`rdbuf`<`getloc` **num_put\<Elem, OutIt>**(`getloc`)**. put**(**OutIt**( ), ** \*this**, , **val**). Aquí, **OutIt** se define como **ostreambuf_iterator\<Elem, Tr>**. La función devuelve ** \*este**archivo .

### <a name="example"></a>Ejemplo

```cpp
// basic_ostream_op_write.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```

## <a name="basic_ostreamoperator"></a><a name="op_eq"></a>basic_ostream::operador ?

Asigna valores del parámetro de objeto `basic_ostream` proporcionado a este objeto.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Referencia `rvalue` a un objeto `basic_ostream`.

### <a name="remarks"></a>Observaciones

El operador miembro llama a swap `(right)`.

## <a name="basic_ostreamput"></a><a name="put"></a>basic_ostream::put

Coloca un carácter en una secuencia.

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>Parámetros

*_Ch*\
Un carácter.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto basic_ostream.

### <a name="remarks"></a>Observaciones

La función de salida sin formato inserta el elemento *_Ch*. Devuelve ** \*este**archivo .

### <a name="example"></a>Ejemplo

```cpp
// basic_ostream_put.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout.put( 'v' );
   cout << endl;
   wcout.put( L'l' );
}
```

```Output
v
l
```

## <a name="basic_ostreamseekp"></a><a name="seekp"></a>basic_ostream::seekp

Restablece la posición en el flujo de salida.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Parámetros

*_Pos*\
Posición en el flujo.

*_Off*\
El desplazamiento relativo a *_Way*.

*_Way*\
Una de las enumeraciones [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir).

### <a name="return-value"></a>Valor devuelto

Referencia al objeto basic_ostream.

### <a name="remarks"></a>Observaciones

Si [fail](../standard-library/basic-ios-class.md#fail) es **false**, la primera función miembro llama a `pos_type` **newpos á** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*), para algún objeto `newpos`temporal . Si `fail` es false, la segunda función llama a **newpos á rdbuf->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(*_Off, _Way*). En cualquier caso,`off_type`si ( )`off_type`**newpos** ( )(-1) (se produce un error en la operación de posicionamiento), la función llama a **istr.** [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Ambas funciones devuelven ** \*este**archivo .

### <a name="example"></a>Ejemplo

```cpp
// basic_ostream_seekp.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main()
{
    using namespace std;
    ofstream x("basic_ostream_seekp.txt");
    streamoff i = x.tellp();
    cout << i << endl;
    x << "testing";
    i = x.tellp();
    cout << i << endl;
    x.seekp(2);   // Put char in third char position in file
    x << " ";

    x.seekp(2, ios::end);   // Put char two after end of file
    x << "z";
}
```

```Output
0
7
```

## <a name="basic_ostreamsentry"></a><a name="sentry"></a>basic_ostream::centinela

La clase anidada describe un objeto cuya declaración estructura las funciones de salida con y sin formato.

clase centinela - público: centinela\<explícito (basic_ostream Elem, Tr>& _Ostr); operador bool() const; ásentry();

### <a name="remarks"></a>Observaciones

La clase anidada describe un objeto cuya declaración estructura las funciones de salida con y sin formato. Si **ostr.**[good](../standard-library/basic-ios-class.md#good) es **True** y **ostr.**[tie](../standard-library/basic-ios-class.md#tie) no es un puntero nulo, el constructor llama a **ostr.tie->**[flush](#flush). A continuación, el constructor `ostr.good` `status`almacena el valor devuelto por en . Una llamada `operator bool` posterior para entregar este valor almacenado.

Si `uncaught_exception` devuelve **False** y [flags](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) es distinto de cero, el destructor llama a [flush](#flush).

## <a name="basic_ostreamswap"></a><a name="swap"></a>basic_ostream::swap

Cambia los valores de este objeto `basic_ostream` por los del objeto `basic_ostream` proporcionado.

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Referencia a un objeto `basic_ostream`.

### <a name="remarks"></a>Observaciones

La función miembro llama [a basic_ios::swap](../standard-library/basic-ios-class.md#swap) `(right)` para intercambiar el contenido de este objeto por el contenido de *right*.

## <a name="basic_ostreamtellp"></a><a name="tellp"></a>basic_ostream::tellp

Notifica la posición en el flujo de salida.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Valor devuelto

Posición en el flujo de salida.

### <a name="remarks"></a>Observaciones

Si [fail](../standard-library/basic-ios-class.md#fail) es **False**, la función miembro devuelve [rdbuf](../standard-library/basic-ios-class.md#rdbuf)**->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **in**). De lo contrario, devuelve `pos_type`(-1).

### <a name="example"></a>Ejemplo

Vea [seekp](#seekp) para obtener un ejemplo de uso de `tellp`.

## <a name="basic_ostreamwrite"></a><a name="write"></a>basic_ostream::escribir

Coloca caracteres en un flujo.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Parámetros

*Contar*\
Recuento de caracteres que se van a colocar en el flujo.

*Str*\
Caracteres que se van a colocar en el flujo.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto basic_ostream.

### <a name="remarks"></a>Observaciones

La función de [salida sin formato](../standard-library/basic-ostream-class.md) inserta la secuencia de elementos *count* a partir de *str*.

### <a name="example"></a>Ejemplo

Vea [streamsize](../standard-library/ios-typedefs.md#streamsize) para obtener un ejemplo de uso de `write`.

## <a name="see-also"></a>Consulte también

[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
