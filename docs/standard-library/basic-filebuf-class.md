---
title: basic_filebuf (Clase)
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
ms.openlocfilehash: 35bed08f2495c971df7f79f62e32b3ff68dfb3d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376882"
---
# <a name="basic_filebuf-class"></a>basic_filebuf (Clase)

Describe un búfer de secuencia que controla la transmisión de elementos de tipo *Char_T*, cuyos rasgos de carácter están determinados por la clase *Tr*, a y desde una secuencia de elementos almacenados en un archivo externo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_filebuf : public basic_streambuf<Char_T, Tr>
```

### <a name="parameters"></a>Parámetros

*Char_T*\
Elemento básico del búfer del archivo.

*Tr*\
Los rasgos del elemento básico del `char_traits<Char_T>`búfer de archivos (normalmente ).

## <a name="remarks"></a>Observaciones

La plantilla de clase describe un búfer de secuencia que controla la transmisión de elementos de tipo *Char_T*, cuyos rasgos de carácter están determinados por la clase *Tr*, a y desde una secuencia de elementos almacenados en un archivo externo.

> [!NOTE]
> Los `basic_filebuf` objetos de tipo se crean con un búfer interno de tipo __char\* __ independientemente del `char_type` especificado por el parámetro de tipo *Char_T*. Esto significa que una cadena Unicode (que contiene **wchar_t** caracteres) se convertirá en una cadena ANSI (que contiene caracteres **char)** antes de que se escriba en el búfer interno. Para almacenar cadenas Unicode en el búfer, cree un nuevo [`basic_streambuf::pubsetbuf`](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` búfer de tipo **wchar_t** y establézquelo con el método. Para ver un ejemplo que muestra este comportamiento, vea a continuación.

Un objeto `basic_filebuf<Char_T, Tr>` de clase almacena un puntero `FILE` de archivo, que designa el objeto que controla la secuencia asociada a un archivo abierto. También almacena punteros a dos facetas de conversión de archivo para su uso por parte de las funciones miembro protegidas [overflow](#overflow) y [underflow](#underflow). Para obtener más [`basic_filebuf::open`](#open)información, consulte .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo forzar un objeto de tipo `basic_filebuf<wchar_t>` para almacenar caracteres Unicode en su búfer interno mediante una llamada al método `pubsetbuf()`.

```cpp
// unicode_basic_filebuf.cpp
// compile with: /EHsc

#include <iostream>
#include <string>
#include <fstream>
#include <iomanip>
#include <memory.h>
#include <string.h>

#define IBUFSIZE 16

using namespace std;

void hexdump(const string& filename);

int main()
{
    wchar_t* wszHello = L"Hello World";
    wchar_t wBuffer[128];

    basic_filebuf<wchar_t> wOutFile;

    // Open a file, wcHello.txt, then write to it, then dump the
    // file's contents in hex
    wOutFile.open("wcHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wcHello.txt\n";
        return -1;
    }
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";
    hexdump(string("wcHello.txt"));

    // Open a file, wwHello.txt, then set the internal buffer of
    // the basic_filebuf object to be of type wchar_t, then write
    // to the file and dump the file's contents in hex
    wOutFile.open("wwHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wwHello.txt\n";
        return -1;
    }
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";
    hexdump(string("wwHello.txt"));

    return 0;
}

// dump contents of filename to stdout in hex
void hexdump(const string& filename)
{
    fstream ifile(filename.c_str(),
        ios_base::in | ios_base::binary);
    char *ibuff = new char[IBUFSIZE];
    char *obuff = new char[(IBUFSIZE*2)+1];
    int i;

    if(!ifile.is_open())
    {
        cout << "Cannot Open " << filename.c_str()
             << " for reading\n";
        return;
    }
    if(!ibuff || !obuff)
    {
        cout << "Cannot Allocate buffers\n";
        ifile.close();
        return;
    }

    while(!ifile.eof())
    {
        memset(obuff,0,(IBUFSIZE*2)+1);
        memset(ibuff,0,IBUFSIZE);
        ifile.read(ibuff,IBUFSIZE);

        // corner case where file is exactly a multiple of
        // 16 bytes in length
        if(ibuff[0] == 0 && ifile.eof())
            break;

        for(i = 0; i < IBUFSIZE; i++)
        {
            if(ibuff[i] >= ' ')
                obuff[i] = ibuff[i];
            else
                obuff[i] = '.';

            cout << setfill('0') << setw(2) << hex
                 << (int)ibuff[i] << ' ';
        }
        cout << "  " << obuff << endl;
    }
    ifile.close();
}
```

```Output
Hex Dump of wcHello.txt - note that output is ANSI chars:
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....

Hex Dump of wwHello.txt - note that output is wchar_t chars:
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........
```

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_filebuf](#basic_filebuf)|Construye un objeto de tipo `basic_filebuf`.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Asocia un nombre de tipo con el parámetro de plantilla `Char_T`.|
|[int_type](#int_type)|Hace que este tipo en el ámbito de `basic_filebuf` equivalga al tipo con el mismo nombre del ámbito `Tr`.|
|[off_type](#off_type)|Hace que este tipo en el ámbito de `basic_filebuf` equivalga al tipo con el mismo nombre del ámbito `Tr`.|
|[pos_type](#pos_type)|Hace que este tipo en el ámbito de `basic_filebuf` equivalga al tipo con el mismo nombre del ámbito `Tr`.|
|[traits_type](#traits_type)|Asocia un nombre de tipo con el parámetro de plantilla `Tr`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Cerca](#close)|Cierra un archivo.|
|[is_open](#is_open)|Indica si un archivo está abierto.|
|[open](#open)|Abre un archivo.|
|[Desbordamiento](#overflow)|Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.|
|[pbackfail](#pbackfail)|La función miembro virtual protegida intenta colocar un elemento en el flujo de entrada y, a continuación, convertirlo en el elemento actual (indicado por el puntero siguiente).|
|[seekoff](#seekoff)|La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.|
|[seekpos](#seekpos)|La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.|
|[setbuf](#setbuf)|La función miembro virtual protegida realiza una determinada operación para cada búfer de secuencia derivado.|
|[Intercambio](#swap)|Intercambia el contenido de `basic_filebuf` por el contenido del parámetro `basic_filebuf` proporcionado.|
|[Sincronizar](#sync)|Función virtual protegida que intenta sincronizar las secuencias controladas con cualquier flujo externo asociado.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Función virtual protegida que extrae el elemento actual de la secuencia de entrada.|
|[Desbordamiento](#underflow)|Función virtual protegida que extrae el elemento actual de la secuencia de entrada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<fstream>

**Espacio de nombres:** std

## <a name="basic_filebufbasic_filebuf"></a><a name="basic_filebuf"></a>basic_filebuf::basic_filebuf

Construye un objeto de tipo `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Observaciones

El primer constructor almacena un puntero nulo en todos los punteros que controlan el búfer de entrada y el de salida. También almacena un puntero nulo en el puntero de archivo.

El segundo constructor inicializa el objeto con el contenido de *right*, tratado como una referencia rvalue.

## <a name="basic_filebufchar_type"></a><a name="char_type"></a>basic_filebuf::char_type

Asocia un nombre de tipo con el parámetro de plantilla `Char_T`.

```cpp
typedef Char_T char_type;
```

## <a name="basic_filebufclose"></a><a name="close"></a>basic_filebuf::cerrar

Cierra un archivo.

```cpp
basic_filebuf<Char_T, Tr> *close();
```

### <a name="return-value"></a>Valor devuelto

La función miembro devuelve un puntero nulo si el puntero de archivo es un puntero nulo.

### <a name="remarks"></a>Observaciones

`close` llama a `fclose(fp)`. Si esa función devuelve un valor distinto de cero, la función devuelve un puntero nulo. De lo contrario, devuelve **this** para indicar que el archivo se ha cerrado correctamente.

Para una secuencia amplia, si se ha producido alguna inserción `streampos`desde que [`overflow`](#overflow)se abrió la secuencia, o desde la última llamada a , la función llama a . También inserta cualquier secuencia necesaria para restaurar el estado de `fac` conversión `fac.unshift` inicial, mediante la faceta de conversión de archivos para llamar según sea necesario. `byte` Cada elemento producido de tipo **char** se escribe en `fp` la secuencia asociada designada `fputc(byte, fp)`por el puntero de archivo como si fuera mediante llamadas sucesivas del formulario . Si se `fac.unshift` produce un error en la llamada o en cualquier escritura, la función no se realiza correctamente.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se supone que hay dos archivos en el directorio actual: *basic_filebuf_close.txt* (contents is "testing") y *iotest.txt* (contents is "ssss").

```cpp
// basic_filebuf_close.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main() {
   using namespace std;
   ifstream file;
   basic_ifstream <wchar_t> wfile;
   char c;
   // Open and close with a basic_filebuf
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );
   file >> c;
   cout << c << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "iotest.txt" );
   file >> c;
   cout << c << endl;
   file.close( );

   // open a file with a wide character name
   wfile.open( L"iotest.txt" );

   // Open and close a nonexistent with a basic_filebuf
   file.rdbuf()->open( "ziotest.txt", ios::in );
   cout << file.fail() << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "ziotest.txt" );
   cout << file.fail() << endl;
   file.close( );
}
```

```Output
t
s
0
1
```

## <a name="basic_filebufint_type"></a><a name="int_type"></a>basic_filebuf::int_type

Hace que `basic_filebuf` este tipo dentro del ámbito sea `Tr` equivalente al tipo del mismo nombre en el ámbito.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_filebufis_open"></a><a name="is_open"></a>basic_filebuf::is_open

Indica si un archivo está abierto.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el puntero de archivo no es null.

### <a name="example"></a>Ejemplo

```cpp
// basic_filebuf_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;

   file.open( "basic_filebuf_is_open.cpp" );
   cout << file.rdbuf( )->is_open( ) << endl;
}
```

```Output
false
true
```

## <a name="basic_filebufoff_type"></a><a name="off_type"></a>basic_filebuf::off_type

Hace que `basic_filebuf` este tipo dentro del ámbito sea `Tr` equivalente al tipo del mismo nombre en el ámbito.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_filebufopen"></a><a name="open"></a>basic_filebuf::abierto

Abre un archivo.

```cpp
basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode);
```

### <a name="parameters"></a>Parámetros

*Nombre*\
Nombre del archivo que se va a abrir.

*Modo*\
Una de las [`ios_base::openmode`](../standard-library/ios-base-class.md#openmode)enumeraciones en .

*Protección*\
La protección de apertura de archivos predeterminada, equivalente al parámetro *shflag* en [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Valor devuelto

Si el búfer ya está abierto, o si el puntero de archivo es un puntero nulo, la función devuelve un puntero nulo. De lo contrario, devuelve **this**.

### <a name="remarks"></a>Observaciones

La función miembro abre el archivo [`fopen`](../c-runtime-library/reference/fopen-wfopen.md) `(filename, strmode)`con el nombre *filename*, llamando a . `strmode`se determina `mode & ~(` [`ate`](../standard-library/ios-base-class.md#openmode) `|` [`binary`](../standard-library/ios-base-class.md#openmode) `)`a partir de:

- `ios_base::in`se `"r"` convierte en (abrir archivo existente para su lectura).

- [ios_base::out](../standard-library/ios-base-class.md#fmtflags) `ios_base::out | ios_base::trunc` o `"w"` se convierte en (truncar el archivo existente o crear para escribir).

- `ios_base::out | app`se `"a"` convierte en (abrir el archivo existente para anexar todas las escrituras).

- `ios_base::in | ios_base::out`se `"r+"` convierte en (abrir archivo existente para leer y escribir).

- `ios_base::in | ios_base::out | ios_base::trunc`se `"w+"` convierte en (truncar el archivo existente o crear para leer y escribir).

- `ios_base::in | ios_base::out | ios_base::app`se `"a+"` convierte en (abrir el archivo existente para leer y para anexar todas las escrituras).

Si `mode & ios_base::binary` es distinto de cero, la función se anexa `b` `strmode` para abrir una secuencia binaria en lugar de una secuencia de texto. A continuación, almacena `fopen` el valor `fp`devuelto por en el puntero de archivo . Si `mode & ios_base::ate` es distinto de cero y el puntero de `fseek(fp, 0, SEEK_END)` archivo no es un puntero nulo, la función llama a colocar la secuencia al final del archivo. Si se produce un error [`close`](#close) `(fp)` en esa operación de posicionamiento, la función llama y almacena un puntero nulo en el puntero de archivo.

Si el puntero de archivo no es un puntero nulo, `use_facet<codecvt<Char_T, char, traits_type::` [`state_type`](../standard-library/char-traits-struct.md#state_type) `> >(` [`getloc`](../standard-library/basic-streambuf-class.md#getloc) `)`la función determina la faceta de conversión de archivos: , para su uso por [subdesbordamiento](#underflow) y [desbordamiento](#overflow).

Si el puntero de archivo es un puntero nulo, la función devuelve un puntero nulo. De lo contrario, devuelve **this**.

### <a name="example"></a>Ejemplo

Consulte [`basic_filebuf::close`](#close) un ejemplo `open`que utiliza .

## <a name="basic_filebufoperator"></a><a name="op_eq"></a>basic_filebuf::operador ?

Asigna el contenido de este objeto de búfer de secuencia. Se trata de una asignación de movimiento que implica un valor r que no deja una copia atrás.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Referencia a un valor R a un objeto [basic_filebuf](../standard-library/basic-filebuf-class.md).

### <a name="return-value"></a>Valor devuelto

Devuelve __*this__.

### <a name="remarks"></a>Observaciones

El operador miembro reemplaza el contenido del objeto mediante el contenido de *right*, tratado como una referencia rvalue. Para obtener más información, vea [Declarator de referencia Rvalue: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="basic_filebufoverflow"></a><a name="overflow"></a>basic_filebuf::desbordamiento

Se llama cuando se inserta un nuevo carácter en un búfer lleno.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parámetros

*_Meta*\
Carácter que se va `traits_type::eof`a insertar en el búfer o .

### <a name="return-value"></a>Valor devuelto

Si la función no se `traits_type::eof`puede realizar correctamente, devuelve . De lo `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)`contrario, devuelve .

### <a name="remarks"></a>Observaciones

Si `_Meta != traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof), la función miembro virtual `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)` protegida intenta insertar el elemento en el búfer de salida. Puede hacerlo de varias maneras:

- Si está disponible una posición de escritura, puede almacenar el elemento en la posición de escritura e incrementar el puntero siguiente para el búfer de salida.

- Puede proporcionar una posición de escritura al asignar almacenamiento nuevo o adicional para el búfer de salida.

- Puede convertir cualquier salida pendiente en el `ch`búfer de salida, `fac` seguido `fac.out` de , mediante la faceta de conversión de archivos para llamar según sea necesario. `ch` Cada elemento producido de tipo *char* se escribe en `fp` la secuencia asociada designada `fputc(ch, fp)`por el puntero de archivo como si fuera mediante llamadas sucesivas del formulario . Si se produce un error en cualquier conversión o escritura, la función no se ejecuta correctamente.

## <a name="basic_filebufpbackfail"></a><a name="pbackfail"></a>basic_filebuf::pbackfail

Intenta volver a colocar un elemento en el flujo de entrada y luego convertirlo en el elemento actual (al que apunta el puntero siguiente).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parámetros

*_Meta*\
El carácter que se va a insertar en el búfer o `traits_type::eof`.

### <a name="return-value"></a>Valor devuelto

Si la función no se `traits_type::eof`puede realizar correctamente, devuelve . De lo `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)`contrario, devuelve .

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida vuelve a colocar un elemento en el búfer de entrada y luego lo convierte en el elemento actual (al que apunta el siguiente puntero). Si `_Meta == traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof), el elemento que se va a insertar es efectivamente el que ya está en la secuencia antes que el elemento actual. De lo contrario, ese `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)`elemento se sustituye por . La función puede devolver un elemento de distintas maneras:

- Si `putback` una posición está disponible y el elemento `ch`almacenado allí se compara igual a , puede disminuir el puntero siguiente para el búfer de entrada.

- Si la función `putback` puede hacer que una posición esté disponible, puede hacerlo, `ch` establecer el puntero siguiente para apuntar a esa posición y almacenar en esa posición.

- Si la función puede insertar un elemento en la secuencia de `ungetc` entrada, puede hacerlo, por ejemplo, llamando a un elemento de tipo **char**.

## <a name="basic_filebufpos_type"></a><a name="pos_type"></a>basic_filebuf::pos_type

Hace que `basic_filebuf` este tipo dentro del ámbito sea `Tr` equivalente al tipo del mismo nombre en el ámbito.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_filebufseekoff"></a><a name="seekoff"></a>basic_filebuf::seekoff

Intenta modificar las posiciones actuales de los flujos controlados.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Off*\
La posición a buscar en relación con *_Way*.

*_Way*\
El punto de partida de las operaciones de desplazamiento. Vea los valores posibles en [seekdir](../standard-library/ios-base-class.md#seekdir).

*_Which*\
Especifica el modo de la posición del puntero. El valor predeterminado es permitirle modificar las posiciones de lectura y escritura.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición nueva o una posición de flujo no válida.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida intenta modificar las posiciones actuales de las secuencias controladas. Para un objeto [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>`de clase , una posición de `fpos_t`secuencia se puede representar mediante un objeto de tipo , que almacena un desplazamiento y cualquier información de estado necesaria para analizar una secuencia amplia. Desplazamiento cero hace referencia al primer elemento de la secuencia. (Un objeto [`pos_type`](../standard-library/basic-streambuf-class.md#pos_type) de tipo `fpos_t` almacena al menos un objeto.)

En el caso de un archivo abierto para lectura y escritura, los flujos de entrada y salida se colocan en tándem. Para cambiar entre insertar y extraer, [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) debe [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)llamar a una o . Las `pubseekoff` llamadas a `seekoff`(y por lo tanto a ) tienen varias limitaciones para [las secuencias](../c-runtime-library/text-and-binary-streams.md)de texto, las [secuencias binarias](../c-runtime-library/text-and-binary-streams.md)y las [secuencias anchas.](../c-runtime-library/byte-and-wide-streams.md)

Si el `fp` puntero de archivo es un puntero nulo, se produce un error en la función. De lo contrario, intenta modificar `fseek(fp, _Off, _Way)`la posición de la secuencia llamando a . Si esa función se `fposn` realiza correctamente `fgetpos(fp, &fposn)`y la posición resultante se puede determinar llamando a , la función se realiza correctamente. Si la función se realiza correctamente, devuelve un valor de tipo `pos_type` que contiene `fposn`. De lo contrario, devuelve una posición de flujo no válida.

## <a name="basic_filebufseekpos"></a><a name="seekpos"></a>basic_filebuf::seekpos

Intenta modificar las posiciones actuales de los flujos controlados.

```cpp
virtual pos_type seekpos(
    pos_type _Sp,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Sp*\
La posición que se va a buscar.

*_Which*\
Especifica el modo de la posición del puntero. El valor predeterminado es permitirle modificar las posiciones de lectura y escritura.

### <a name="return-value"></a>Valor devuelto

Si el `fp` puntero de archivo es un puntero nulo, se produce un error en la función. De lo contrario, intenta modificar `fsetpos(fp, &fposn)`la `fposn` posición `fpos_t` de la `pos`secuencia llamando a , donde está el objeto almacenado en . Si esa función se ejecuta correctamente, la función devuelve `pos`. De lo contrario, devuelve una posición de flujo no válida. Para determinar si la posición del flujo no es válida, compare el valor devuelto con `pos_type(off_type(-1))`.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida intenta modificar las posiciones actuales de las secuencias controladas. Para un objeto [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>`de clase , una posición de `fpos_t`secuencia se puede representar mediante un objeto de tipo , que almacena un desplazamiento y cualquier información de estado necesaria para analizar una secuencia amplia. Desplazamiento cero hace referencia al primer elemento de la secuencia. (Un objeto de tipo `pos_type` almacena al menos un objeto `fpos_t`).

En el caso de un archivo abierto para lectura y escritura, los flujos de entrada y salida se colocan en tándem. Para cambiar entre insertar y extraer, [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) debe [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)llamar a una o . Las `pubseekoff` llamadas `seekoff`a (y a ) tienen varias limitaciones para secuencias de texto, secuencias binarias y secuencias anchas.

En un flujo ancho, si se han producido inserciones desde la apertura del flujo o desde la última llamada a `streampos`, la función llama a [overflow](#overflow). También inserta cualquier secuencia necesaria para restaurar el estado de `fac` conversión `fac.unshift` inicial, mediante la faceta de conversión de archivos para llamar según sea necesario. `byte` Cada elemento producido de tipo **char** se escribe en `fp` la secuencia asociada designada `fputc(byte, fp)`por el puntero de archivo como si fuera mediante llamadas sucesivas del formulario . Si se `fac.unshift` produce un error en la llamada o en cualquier escritura, la función no se realiza correctamente.

## <a name="basic_filebufsetbuf"></a><a name="setbuf"></a>basic_filebuf::setbuf

Realiza una determinada operación para cada búfer de flujo derivado.

```cpp
virtual basic_streambuf<Char_T, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parámetros

*_Buffer*\
Puntero a un búfer.

*Contar*\
Tamaño del búfer.

### <a name="return-value"></a>Valor devuelto

La función miembro protegida devuelve cero si el puntero de archivo `fp` es un puntero nulo.

### <a name="remarks"></a>Observaciones

`setbuf`llama `setvbuf( fp, (char*) _Buffer, _IOFBF, count * sizeof( Char_T))` para ofrecer `count` la matriz de elementos que comienzan en *_Buffer* como búfer para la secuencia. Si esa función devuelve un valor distinto de cero, la función devuelve un puntero nulo. De lo contrario, devuelve **this** para señalar el éxito.

## <a name="basic_filebufswap"></a><a name="swap"></a>basic_filebuf::swap

Intercambia el contenido de este `basic_filebuf` por el contenido del `basic_filebuf` proporcionado.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Una referencia lvalue `basic_filebuf`a otro archivo .

## <a name="basic_filebufsync"></a><a name="sync"></a>basic_filebuf::sync

Intenta sincronizar los flujos controlados con cualquier flujo externo asociado.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Valor devuelto

Devuelve cero si `fp` el puntero de archivo es un puntero nulo. De lo contrario, devuelve cero solo `fflush(fp)` si las llamadas a ambos se [desbordan](#overflow) y se realizan correctamente en la salida pendiente de la secuencia.

## <a name="basic_filebuftraits_type"></a><a name="traits_type"></a>basic_filebuf::traits_type

Asocia un nombre de tipo con el parámetro de plantilla `Tr`.

```cpp
typedef Tr traits_type;
```

## <a name="basic_filebufunderflow"></a><a name="underflow"></a>basic_filebuf::underflow

Extrae el elemento actual del flujo de entrada.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Valor devuelto

Si la función no se `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)puede realizar correctamente, devuelve . De lo `ch`contrario, devuelve , convertido como se describe en la sección Comentarios.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida `ch` intenta extraer el elemento actual `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(ch)`de la secuencia de entrada y devolver el elemento como . Puede hacerlo de varias maneras:

- Si una posición de lectura `ch` está disponible, toma como el elemento almacenado en la posición de lectura y avanza el puntero siguiente para el búfer de entrada.

- Puede leer uno o más elementos de tipo **char** `fgetc(fp)`, como si por `ch` llamadas sucesivas del formulario , y convertirlos en un elemento de tipo `Char_T` mediante la faceta `fac` de conversión de archivos para llamar `fac.in` según sea necesario. Si se produce un error en cualquier conversión o lectura, la función no se ejecuta correctamente.

## <a name="see-also"></a>Consulte también

[\<>fstream](../standard-library/fstream.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
