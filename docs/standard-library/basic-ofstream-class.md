---
title: basic_ofstream (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31637c1c194754e193970a4ff5efef500228115b
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105255"
---
# <a name="basicofstream-class"></a>basic_ofstream (Clase)

Describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de flujo de la clase [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

*Elem*<br/>
Elemento básico del búfer del archivo.

*Tr*<br/>
Rasgos del elemento básico del búfer del archivo (normalmente `char_traits`< `Elem`>).

## <a name="remarks"></a>Comentarios

Cuando el **wchar_t** especialización de `basic_ofstream` escribe en el archivo, si el archivo se abre en modo de texto escribirá una secuencia MBCS. La representación interna usará un búfer de caracteres `wchar_t`.

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
|[basic_ofstream](#basic_ofstream)|Crea un objeto del tipo `basic_ofstream`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[close](#close)|Cierra un archivo.|
|[is_open](#is_open)|Determina si un archivo está abierto.|
|[open](#open)|Abre un archivo.|
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer de secuencia almacenado.|
|[swap](#swap)|Intercambia el contenido de este `basic_ofstream` con el contenido del `basic_ofstream` proporcionado.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator=](#op_eq)|Asigna el contenido de este objeto de secuencia. Se trata de una asignación de movimiento que implica un `rvalue reference` que no deja ninguna copia atrás.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<fstream>

**Espacio de nombres:** std

## <a name="basic_ofstream"></a>  basic_ofstream::basic_ofstream

Crea un objeto del tipo `basic_ofstream`.

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

*_Nombre de archivo*<br/>
Nombre del archivo que se va a abrir.

*_Modo de*<br/>
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Protección predeterminada de apertura del archivo, equivalente al parámetro `shflag` de [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

*right*<br/>
Referencia a un valor R al objeto `basic_ofstream` que se usa para inicializar este objeto `basic_ofstream`.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa la clase base mediante una llamada a [basic_ostream](../standard-library/basic-ostream-class.md)(`sb`), donde `sb` es el objeto almacenado de clase [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem`, `Tr`>. También inicializa `sb` al llamar a `basic_filebuf`< `Elem`, `Tr`>.

El segundo y el tercer constructor inicializan la clase base al llamar a `basic_ostream`(**sb**). También inicializa `sb` mediante una llamada a `basic_filebuf` <  `Elem`, `Tr`> y, a continuación, `sb`. [open](../standard-library/basic-filebuf-class.md#open)(`_Filename`, `_Mode` &#124; `ios_base::out`). Si esta última función devuelve un puntero nulo, el constructor llama a [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

El cuarto constructor es una función de copia. Inicializa el objeto con el contenido de *derecho*, tratado como una referencia rvalue.

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

## <a name="close"></a>  basic_ofstream::close

Cierra un archivo.

```cpp
void close();
```

### <a name="remarks"></a>Comentarios

La función miembro llama a [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf)**->**[cerrar](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo de uso de `close`.

## <a name="is_open"></a>  basic_ofstream::is_open

Indica si un archivo está abierto.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el archivo está abierto, **False** en caso contrario.

### <a name="remarks"></a>Comentarios

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

## <a name="open"></a>  basic_ofstream::open

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

*_Nombre de archivo*<br/>
Nombre del archivo que se va a abrir.

*_Modo de*<br/>
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Protección predeterminada de apertura del archivo, equivalente al parámetro `shflag` de [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Comentarios

La función miembro llama a [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; `ios_base::out`). Si esa función devuelve un puntero nulo, la función llama a [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

### <a name="example"></a>Ejemplo

Consulte [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) para obtener un ejemplo que usa `open`.

## <a name="op_eq"></a>  basic_ofstream::operator=

Asigna el contenido de este objeto de secuencia. Se trata de una asignación de movimiento que implica un `rvalue reference` que no deja ninguna copia atrás.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
Referencia a un valor R a un objeto `basic_ofstream`.

### <a name="return-value"></a>Valor devuelto

Devuelve `*this`.

### <a name="remarks"></a>Comentarios

El operador miembro reemplaza el contenido del objeto mediante los contenidos de *derecho*, tratado como una referencia rvalue.

## <a name="rdbuf"></a>  basic_ofstream::rdbuf

Devuelve la dirección del búfer de secuencia almacenado.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección del búfer de secuencia almacenado.

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa `rdbuf`.

## <a name="swap"></a>  basic_ofstream::swap

Intercambia el contenido de dos objetos `basic_ofstream`.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
Referencia `lvalue` a otro objeto `basic_ofstream`.

### <a name="remarks"></a>Comentarios

La función miembro intercambia el contenido de este objeto para el contenido de *derecho*.

## <a name="see-also"></a>Vea también

[basic_ostream (Clase)](../standard-library/basic-ostream-class.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
