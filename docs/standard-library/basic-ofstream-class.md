---
title: basic_ofstream (Clase)
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
ms.openlocfilehash: f2d0facd92e0ef1935f8218a6d323a62edb81e5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376793"
---
# <a name="basic_ofstream-class"></a>basic_ofstream (Clase)

Describe un objeto que controla la inserción de elementos y objetos `Elem`codificados en un búfer `Tr`de secuencia de la clase [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, con elementos de tipo , cuyos rasgos de carácter están determinados por la clase .

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

*Elem*\
Elemento básico del búfer del archivo.

*Tr*\
Rasgos del elemento básico del búfer del archivo (normalmente `char_traits`< `Elem`>).

## <a name="remarks"></a>Observaciones

Cuando **wchar_t** el wchar_t `basic_ofstream` especialización de escrituras en el archivo, si el archivo se abre en modo de texto, escribirá una secuencia MBCS. La representación interna usará un búfer de caracteres `wchar_t`.

El objeto almacena un objeto de clase `basic_filebuf`< `Elem`, `Tr`>.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo de código se muestra cómo crear un objeto `basic_ofstream` y escribir texto en él.

```cpp
// basic_ofstream_class.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_ofstream](#basic_ofstream)|Crea un objeto de tipo `basic_ofstream`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Cerca](#close)|Cierra un archivo.|
|[is_open](#is_open)|Determina si un archivo está abierto.|
|[open](#open)|Abre un archivo.|
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer de secuencia almacenado.|
|[swap](#swap)|Intercambia el contenido de este `basic_ofstream` con el contenido del `basic_ofstream` proporcionado.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador](#op_eq)|Asigna el contenido de este objeto de secuencia. Se trata de una asignación de movimiento que implica un `rvalue reference` que no deja ninguna copia atrás.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<fstream>

**Espacio de nombres:** std

## <a name="basic_ofstreambasic_ofstream"></a><a name="basic_ofstream"></a>basic_ofstream::basic_ofstream

Crea un objeto de tipo `basic_ofstream`.

```cpp
basic_ofstream();

explicit basic_ofstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ofstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_ofstream(
    basic_ofstream&& right);
```

### <a name="parameters"></a>Parámetros

*_Filename*\
Nombre del archivo que se va a abrir.

*_Mode*\
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Protección predeterminada de apertura del archivo, equivalente al parámetro `shflag` de [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

*Correcto*\
Referencia a un valor R al objeto `basic_ofstream` que se usa para inicializar este objeto `basic_ofstream`.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa la [basic_ostream](../standard-library/basic-ostream-class.md)clase`sb`base `sb` llamando a basic_ostream ( `Tr` ), donde está el objeto almacenado de la clase [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`,>. También inicializa `sb` al llamar a `basic_filebuf`< `Elem`, `Tr`>.

El segundo y el tercer constructor inicializan la clase base al llamar a `basic_ostream`(**sb**). También se `sb` inicializa `basic_filebuf` <  `Elem`llamando `Tr` a `sb`,> y, a continuación, . [abierto](../standard-library/basic-filebuf-class.md#open) `_Filename`( `_Mode` `ios_base::out`, &#124; ). Si esta última función devuelve un puntero`failbit`nulo, el constructor llama a [setstate](../standard-library/basic-ios-class.md#setstate)( ).

El cuarto constructor es una función de copia. Inicializa el objeto con el contenido de *right*, tratado como una referencia rvalue.

### <a name="example"></a>Ejemplo

En el siguiente ejemplo de código se muestra cómo crear un objeto `basic_ofstream` y escribir texto en él.

```cpp
// basic_ofstream_ctor.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("C:\\ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

## <a name="basic_ofstreamclose"></a><a name="close"></a>basic_ofstream::cerrar

Cierra un archivo.

```cpp
void close();
```

### <a name="remarks"></a>Observaciones

La función miembro llama [a rdbuf](../standard-library/basic-ifstream-class.md#rdbuf)**->**[close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa `close`.

## <a name="basic_ofstreamis_open"></a><a name="is_open"></a>basic_ofstream::is_open

Indica si un archivo está abierto.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el archivo está abierto, **False** en caso contrario.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Ejemplo

```cpp
// basic_ofstream_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   // Open and close with a basic_filebuf
   file.rdbuf( )->open( "basic_ofstream_is_open.txt", ios::in );
   file.close( );
   if (file.is_open())
      cout << "it's open" << endl;
   else
      cout << "it's closed" << endl;
}
```

## <a name="basic_ofstreamopen"></a><a name="open"></a>basic_ofstream::abierto

Abre un archivo.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Parámetros

*_Filename*\
Nombre del archivo que se va a abrir.

*_Mode*\
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Protección predeterminada de apertura del archivo, equivalente al parámetro `shflag` de [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Observaciones

La función miembro llama a `_Mode` [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, &#124; `ios_base::out`). Si esa función devuelve un puntero`failbit`nulo, la función llama a [setstate](../standard-library/basic-ios-class.md#setstate)( ).

### <a name="example"></a>Ejemplo

Consulte [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) para ver `open`un ejemplo que utiliza .

## <a name="basic_ofstreamoperator"></a><a name="op_eq"></a>basic_ofstream::operador ?

Asigna el contenido de este objeto de secuencia. Se trata de una asignación de movimiento que implica un `rvalue reference` que no deja ninguna copia atrás.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Referencia a un valor R a un objeto `basic_ofstream`.

### <a name="return-value"></a>Valor devuelto

Devuelve `*this`.

### <a name="remarks"></a>Observaciones

El operador miembro reemplaza el contenido del objeto mediante el contenido de *right*, tratado como una referencia rvalue.

## <a name="basic_ofstreamrdbuf"></a><a name="rdbuf"></a>basic_ofstream::rdbuf

Devuelve la dirección del búfer de secuencia almacenado.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección del búfer de secuencia almacenado.

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa `rdbuf`.

## <a name="basic_ofstreamswap"></a><a name="swap"></a>basic_ofstream::swap

Intercambia el contenido de dos objetos `basic_ofstream`.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Referencia `lvalue` a otro objeto `basic_ofstream`.

### <a name="remarks"></a>Observaciones

La función miembro intercambia el contenido de este objeto por el contenido de *right*.

## <a name="see-also"></a>Consulte también

[Clase basic_ostream](../standard-library/basic-ostream-class.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
