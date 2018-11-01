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
ms.openlocfilehash: 30ae1e6384b3861bc4324d42f095516f80dce6e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577325"
---
# <a name="basicifstream-class"></a>basic_ifstream (Clase)

Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo de clase [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

*Elem*<br/>
Elemento básico del búfer del archivo.

*Tr*<br/>
Rasgos del elemento básico del búfer del archivo (normalmente `char_traits`< `Elem`>).

## <a name="remarks"></a>Comentarios

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

## <a name="input-basicifstreamclasstxt"></a>Entrada: basic_ifstream_class.txt

```cpp
This is the contents of basic_ifstream_class.txt.
```

## <a name="output"></a>Resultados

```cpp
This is the contents of basic_ifstream_class.txt.
```

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_ifstream](#basic_ifstream)|Inicializa una nueva instancia de un objeto `basic_ifstream`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[close](#close)|Cierra un archivo.|
|[is_open](#is_open)|Determina si un archivo está abierto.|
|[open](#open)|Abre un archivo.|
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer de secuencia almacenado.|
|[swap](#swap)|Intercambia el contenido de `basic_ifstream` por el contenido del `basic_ifstream` proporcionado.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator=](#op_eq)|Asigna el contenido de este objeto de secuencia. Se trata de una asignación de movimiento que implica un `rvalue` que no deja ninguna copia atrás.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<fstream>

**Espacio de nombres:** std

## <a name="basic_ifstream"></a>  basic_ifstream::basic_ifstream

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

*_Nombre de archivo*<br/>
Nombre del archivo que se va a abrir.

*_Modo de*<br/>
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Protección predeterminada de apertura del archivo, equivalente al parámetro `shflag` de [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Comentarios

El primer constructor inicializa la clase base al llamar a [basic_istream](../standard-library/basic-istream-class.md)(`sb`), donde `sb` es el objeto almacenado de clase [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>. También inicializa `sb` al llamar a `basic_filebuf`< `Elem`, `Tr`>.

El segundo y el tercer constructor inicializan la clase base al llamar a `basic_istream`(`sb`). También inicializa `sb` al llamar a [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`> y luego a `sb`. [open](../standard-library/basic-filebuf-class.md#open)(`_Filename`, `_Mode` &#124; `ios_base::in`). Si esta última función devuelve un puntero nulo, el constructor llama a **setstate**(`failbit`).

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

## <a name="close"></a>  basic_ifstream::close

Cierra un archivo.

```cpp
void close();
```

### <a name="remarks"></a>Comentarios

La función miembro llama a [rdbuf](#rdbuf) **->** [cerrar](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo de uso de `close`.

## <a name="is_open"></a>  basic_ifstream::is_open

Determina si un archivo está abierto.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el archivo está abierto, **False** en caso contrario.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) para obtener un ejemplo que usa `is_open`.

## <a name="open"></a>  basic_ifstream::open

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

*_Nombre de archivo*<br/>
Nombre del archivo que se va a abrir.

*_Modo de*<br/>
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Protección predeterminada de apertura del archivo, equivalente al parámetro `shflag` de [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Comentarios

La función miembro llama a [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; **ios_base::in**). Si open produce un error, las llamadas de función [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`), que puede producir una excepción ios_base:: Failure.

### <a name="example"></a>Ejemplo

Consulte [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) para obtener un ejemplo que usa `open`.

## <a name="op_eq"></a>  basic_ifstream::operator=

Asigna el contenido de este objeto de secuencia. Se trata de una asignación de movimiento que implica un valor R que no deja ninguna copia atrás.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
Referencia a un valor R a un objeto `basic_ifstream`.

### <a name="return-value"></a>Valor devuelto

Devuelve `*this`.

### <a name="remarks"></a>Comentarios

El operador miembro reemplaza el contenido del objeto mediante los contenidos de *derecho*, tratado como una referencia rvalue. Para más información, vea [Lvalues y rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="rdbuf"></a>  basic_ifstream::rdbuf

Devuelve la dirección del búfer de secuencia almacenado.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto [basic_filebuf](../standard-library/basic-filebuf-class.md) que representa el búfer de flujo almacenado.

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo de uso de `rdbuf`.

## <a name="swap"></a>  basic_ifstream::swap

Intercambia el contenido de dos objetos `basic_ifstream`.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
Referencia a otro búfer de secuencia.

### <a name="remarks"></a>Comentarios

La función miembro intercambia el contenido de este objeto para el contenido de *derecho*.

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
