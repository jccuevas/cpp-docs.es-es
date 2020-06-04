---
title: basic_ifstream (Clase)
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
helpviewer_keywords:
- std::basic_ifstream [C++]
- std::basic_ifstream [C++], close
- std::basic_ifstream [C++], is_open
- std::basic_ifstream [C++], open
- std::basic_ifstream [C++], rdbuf
- std::basic_ifstream [C++], swap
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
ms.openlocfilehash: 85a315ee393a002da4d0999569d4af6c34a37ee3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376842"
---
# <a name="basic_ifstream-class"></a>basic_ifstream (Clase)

Describe un objeto que controla la extracción de elementos `Tr` y objetos `Elem`codificados desde un búfer de secuencia de la clase [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`,>, con elementos de tipo , cuyos rasgos de carácter están determinados por la clase `Tr`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

*Elem*\
Elemento básico del búfer del archivo.

*Tr*\
Rasgos del elemento básico del búfer del archivo (normalmente `char_traits`< `Elem`>).

## <a name="remarks"></a>Observaciones

El objeto almacena un objeto de clase `basic_filebuf`< `Elem`, `Tr`>.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo leer texto de un archivo.

```cpp
// basic_ifstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_class.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="input-basic_ifstream_classtxt"></a>Entrada: basic_ifstream_class.txt

```cpp
This is the contents of basic_ifstream_class.txt.
```

## <a name="output"></a>Output

```cpp
This is the contents of basic_ifstream_class.txt.
```

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_ifstream](#basic_ifstream)|Inicializa una nueva instancia de un objeto `basic_ifstream`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Cerca](#close)|Cierra un archivo.|
|[is_open](#is_open)|Determina si un archivo está abierto.|
|[open](#open)|Abre un archivo.|
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer de secuencia almacenado.|
|[swap](#swap)|Intercambia el contenido de `basic_ifstream` por el contenido del `basic_ifstream` proporcionado.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador](#op_eq)|Asigna el contenido de este objeto de secuencia. Se trata de una asignación de movimiento que implica un `rvalue` que no deja ninguna copia atrás.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<fstream>

**Espacio de nombres:** std

## <a name="basic_ifstreambasic_ifstream"></a><a name="basic_ifstream"></a>basic_ifstream::basic_ifstream

Construye un objeto de tipo `basic_ifstream`.

```cpp
basic_ifstream();

explicit basic_ifstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ifstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

basic_ifstream(basic_ifstream&& right);
```

### <a name="parameters"></a>Parámetros

*_Filename*\
Nombre del archivo que se va a abrir.

*_Mode*\
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Protección predeterminada de apertura del archivo, equivalente al parámetro `shflag` de [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Observaciones

El primer constructor inicializa la [basic_istream](../standard-library/basic-istream-class.md)clase `sb`base `sb` llamando a basic_istream ( `Tr` ), donde está el objeto almacenado de la clase [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`,>. También inicializa `sb` al llamar a `basic_filebuf`< `Elem`, `Tr`>.

El segundo y el tercer constructor inicializan la clase base al llamar a `basic_istream`(`sb`). También se `sb` inicializa llamando `Tr` a [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`,> y, a continuación, `sb`. [abierto](../standard-library/basic-filebuf-class.md#open) `_Filename`( `_Mode` `ios_base::in`, &#124; ). Si esta última función devuelve un puntero `failbit`nulo, el constructor llama a **setstate**( ).

El cuarto constructor inicializa el objeto con el contenido de `right`, tratado como una referencia a un valor R.

### <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo leer texto de un archivo. Para crear el archivo, vea el ejemplo de [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

```cpp
// basic_ifstream_ctor.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_ctor.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="basic_ifstreamclose"></a><a name="close"></a>basic_ifstream::cerrar

Cierra un archivo.

```cpp
void close();
```

### <a name="remarks"></a>Observaciones

La función miembro llama [a rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa `close`.

## <a name="basic_ifstreamis_open"></a><a name="is_open"></a>basic_ifstream::is_open

Determina si un archivo está abierto.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el archivo está abierto, **False** en caso contrario.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) para obtener un ejemplo que usa `is_open`.

## <a name="basic_ifstreamopen"></a><a name="open"></a>basic_ifstream::abierto

Abre un archivo.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
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

La función miembro llama a `_Mode` [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, &#124; **ios_base::in**). Si se produce un error`failbit`en open, la función llama a [setstate](../standard-library/basic-ios-class.md#setstate)( ), lo que puede producir una excepción ios_base::failure.

### <a name="example"></a>Ejemplo

Consulte [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) para ver `open`un ejemplo que utiliza .

## <a name="basic_ifstreamoperator"></a><a name="op_eq"></a>basic_ifstream::operador ?

Asigna el contenido de este objeto de secuencia. Se trata de una asignación de movimiento que implica un valor R que no deja ninguna copia atrás.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Referencia a un valor R a un objeto `basic_ifstream`.

### <a name="return-value"></a>Valor devuelto

Devuelve `*this`.

### <a name="remarks"></a>Observaciones

El operador miembro reemplaza el contenido del objeto mediante el contenido de *right*, tratado como una referencia rvalue. Para más información, vea [Lvalues y rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="basic_ifstreamrdbuf"></a><a name="rdbuf"></a>basic_ifstream::rdbuf

Devuelve la dirección del búfer de secuencia almacenado.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto [basic_filebuf](../standard-library/basic-filebuf-class.md) que representa el búfer de flujo almacenado.

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa `rdbuf`.

## <a name="basic_ifstreamswap"></a><a name="swap"></a>basic_ifstream::swap

Intercambia el contenido de dos objetos `basic_ifstream`.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Referencia a otro búfer de secuencia.

### <a name="remarks"></a>Observaciones

La función miembro intercambia el contenido de este objeto por el contenido de *right*.

## <a name="see-also"></a>Consulte también

[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
