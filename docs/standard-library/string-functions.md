---
title: Funciones &lt;string&gt;
ms.date: 11/04/2016
f1_keywords:
- string/std::getline
- string/std::stod
- string/std::stof
- string/std::stoi
- string/std::stol
- string/std::stold
- string/std::stoll
- string/std::stoul
- string/std::stoull
- string/std::swap
- string/std::to_string
- string/std::to_wstring
ms.assetid: 1a4ffd11-dce5-4cc6-a043-b95de034c7c4
helpviewer_keywords:
- std::getline [C++]
- std::stod [C++]
- std::stof [C++]
- std::stoi [C++]
- std::stol [C++]
- std::stold [C++]
- std::stoll [C++]
- std::stoul [C++]
- std::stoull [C++]
- std::swap [C++]
- std::to_string [C++]
- std::to_wstring [C++]
ms.openlocfilehash: dbcc4a86731bba092d8358a046fd3f9eb949f91f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214973"
---
# <a name="ltstringgt-functions"></a>Funciones &lt;string&gt;

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a><a name="getline"></a>  getline

Extraiga las cadenas de la secuencia de entrada línea por línea.

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delimiter);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delimiter);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& in_stream,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parámetros

*in_stream*\
La secuencia de entrada de la que se extraerá una cadena.

\ *Str*
La cadena en la que se leen los caracteres de la secuencia de entrada.

*delimitador*\
El delimitador de línea.

### <a name="return-value"></a>Valor devuelto

El flujo de entrada *in_stream*.

### <a name="remarks"></a>Observaciones

El par de firmas de función marcadas `(1)` extraer caracteres de *in_stream* hasta que se encuentre el *delimitador* , almacenándolos en *Str*.

El par de firmas de función marcadas `(2)` usar newline como el delimitador de línea predeterminado y se comporta como `getline(in_stream, str, in_stream. widen('\n'))`.

La segunda función de cada par es análoga a la primera para admitir las [referencias rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

La extracción se detiene en los siguientes casos:

- Al final del archivo, en cuyo caso la marca de estado interno de *in_stream* se establece en `ios_base::eofbit`.

- Después de que la función extraiga un elemento que se compare con el *delimitador*de igualdad. El elemento no se vuelve a colocar ni se anexa a la secuencia controlada.

- Después de que la función Extraiga `str.`elementos [max_size](../standard-library/basic-string-class.md#max_size) . La marca de estado interno de *in_stream* se establece en `ios_base::failbit`.

- Otro error distinto de los enumerados anteriormente; la marca de estado interno de *in_stream* se establece en `ios_base::badbit`.

Para obtener información sobre las marcas de estado interno, vea [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Si la función no extrae ningún elemento, la marca de estado interno de *in_stream* se establece en `ios_base::failbit`. En cualquier caso, `getline` devuelve *in_stream*.

Si se produce una excepción, *in_stream* y *Str* se dejan en un estado válido.

### <a name="example"></a>Ejemplo

El código siguiente muestra `getline()` en dos modos: primero, con el delimitador predeterminado (nueva línea) y, después, con un espacio en blanco como delimitador. El carácter de fin de archivo (CTRL-Z en el teclado) se utiliza para controlar la terminación de los bucles while. Este valor establece la marca de estado interno de `cin` en `eofbit`, que se debe borrar con [basic_ios:: CLEAR ()](../standard-library/basic-ios-class.md#clear) antes de que el segundo bucle while funcione correctamente.

```cpp
// compile with: /EHsc /W4
#include <string>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    string str;
    vector<string> v1;
    cout << "Enter a sentence, press ENTER between sentences. (Ctrl-Z to stop): " << endl;
    // Loop until end-of-file (Ctrl-Z) is input, store each sentence in a vector.
    // Default delimiter is the newline character.
    while (getline(cin, str)) {
        v1.push_back(str);
    }

    cout << "The following input was stored with newline delimiter:" << endl;
    for (const auto& p : v1) {
        cout << p << endl;
    }

    cin.clear();

    vector<string> v2;
    // Now try it with a whitespace delimiter
    while (getline(cin, str, ' ')) {
        v2.push_back(str);
    }

    cout << "The following input was stored with whitespace as delimiter:" << endl;
    for (const auto& p : v2) {
        cout << p << endl;
    }
}
```

## <a name="stod"></a><a name="stod"></a>  stod

Convierte una secuencia de caracteres en una **`double`** .

```cpp
double stod(
    const string& str,
    size_t* idx = 0);

double stod(
    const wstring& str,
    size_t* idx = 0
;
```

### <a name="parameters"></a>Parámetros

\ *Str*
La secuencia de caracteres que se convertirá.

\ *IDX*
El valor del índice del primer carácter que no se convertirá.

### <a name="return-value"></a>Valor devuelto

Valor de **`double`** .

### <a name="remarks"></a>Observaciones

La función convierte la secuencia de elementos de *Str* en un valor de tipo **`double`** como si se llamara a `strtod( str.c_str(), _Eptr)`, donde `_Eptr` es un objeto interno de la función. Si `str.c_str() == *_Eptr`, lanza un objeto de tipo `invalid_argument`. Si esa llamada, al ejecutarse, establecería `errno`, lanza un objeto de tipo `out_of_range`. De lo contrario, si *IDX* no es un puntero nulo, la función almacena `*_Eptr -  str.c_str()` en `*idx` y devuelve el valor.

## <a name="stof"></a><a name="stof"></a>  stof

Convierte una secuencia de caracteres en un float.

```cpp
float stof(
    const string& str,
    size_t* idx = 0);

float stof(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parámetros

\ *Str*
La secuencia de caracteres que se convertirá.

\ *IDX*
El valor del índice del primer carácter que no se convertirá.

### <a name="return-value"></a>Valor devuelto

Valor de **`float`** .

### <a name="remarks"></a>Observaciones

La función convierte la secuencia de elementos de *Str* en un valor de tipo **`float`** como si se llamara a `strtof( str.c_str(), _Eptr)`, donde `_Eptr` es un objeto interno de la función. Si `str.c_str() == *_Eptr`, lanza un objeto de tipo `invalid_argument`. Si esa llamada, al ejecutarse, establecería `errno`, lanza un objeto de tipo `out_of_range`. De lo contrario, si *IDX* no es un puntero nulo, la función almacena `*_Eptr -  str.c_str()` en `*idx` y devuelve el valor.

## <a name="stoi"></a><a name="stoi"></a>  stoi

Convierte una secuencia de caracteres en un entero.

```cpp
int stoi(
    const string& str,
    size_t* idx = 0,
    int base = 10);

int stoi(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="return-value"></a>Valor devuelto

El valor del entero.

### <a name="parameters"></a>Parámetros

\ *Str*
La secuencia de caracteres que se convertirá.

\ *IDX*
El valor del índice del primer carácter que no se convertirá.

*base*\
La base numérica que se usará.

### <a name="remarks"></a>Observaciones

La función `stoi` convierte la secuencia de caracteres de *Str* en un valor de tipo **`int`** y devuelve el valor. Por ejemplo, cuando se pasa la secuencia de caracteres “10”, el valor devuelto por `stoi` es el número entero 10.

`stoi` se comporta de forma similar a la función `strtol` para caracteres de un solo byte cuando se llama de la manera `strtol( str.c_str(), _Eptr, idx)`, donde `_Eptr` es un objeto interno de la función; o `wcstol` para caracteres anchos, cuando se llama de manera similar, `wcstol(Str.c_str(), _Eptr, idx)`. Para más información, vea [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Si `str.c_str() == *_Eptr`, `stoi` produce un objeto de tipo `invalid_argument`. Si dicha llamada establecera `errno`, o si el valor devuelto no se puede representar como un objeto de tipo **`int`** , produce un objeto de tipo `out_of_range`. De lo contrario, si *IDX* no es un puntero nulo, la función almacena `*_Eptr - str.c_str()` en `*idx`.

## <a name="stol"></a><a name="stol"></a>  stol

Convierte una secuencia de caracteres en una **`long`** .

```cpp
long stol(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long stol(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parámetros

\ *Str*
La secuencia de caracteres que se convertirá.

\ *IDX*
El valor del índice del primer carácter que no se convertirá.

*base*\
La base numérica que se usará.

### <a name="return-value"></a>Valor devuelto

El valor de entero largo.

### <a name="remarks"></a>Observaciones

La función convierte la secuencia de elementos de *Str* en un valor de tipo **`long`** como si se llamara a `strtol( str.c_str(), _Eptr, idx)`, donde `_Eptr` es un objeto interno de la función. Si `str.c_str() == *_Eptr`, lanza un objeto de tipo `invalid_argument`. Si esa llamada, al ejecutarse, establecería `errno`, lanza un objeto de tipo `out_of_range`. De lo contrario, si *IDX* no es un puntero nulo, la función almacena `*_Eptr -  str.c_str()` en `*idx` y devuelve el valor.

## <a name="stold"></a><a name="stold"></a>  stold

Convierte una secuencia de caracteres en una **`long double`** .

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parámetros

\ *Str*
La secuencia de caracteres que se convertirá.

\ *IDX*
El valor del índice del primer carácter que no se convertirá.

### <a name="return-value"></a>Valor devuelto

Valor de **`long double`** .

### <a name="remarks"></a>Observaciones

La función convierte la secuencia de elementos de *Str* en un valor de tipo **`long double`** como si se llamara a `strtold( str.c_str(), _Eptr)`, donde `_Eptr` es un objeto interno de la función. Si `str.c_str() == *_Eptr`, lanza un objeto de tipo `invalid_argument`. Si esa llamada, al ejecutarse, establecería `errno`, lanza un objeto de tipo `out_of_range`. De lo contrario, si *IDX* no es un puntero nulo, la función almacena `*_Eptr -  str.c_str()` en `*idx` y devuelve el valor.

## <a name="stoll"></a><a name="stoll"></a>  stoll

Convierte una secuencia de caracteres en una **`long long`** .

```cpp
long long stoll(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long long stoll(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parámetros

\ *Str*
La secuencia de caracteres que se convertirá.

\ *IDX*
El valor del índice del primer carácter que no se convertirá.

*base*\
La base numérica que se usará.

### <a name="return-value"></a>Valor devuelto

Valor de **`long long`** .

### <a name="remarks"></a>Observaciones

La función convierte la secuencia de elementos de *Str* en un valor de tipo **`long long`** como si se llamara a `strtoll( str.c_str(), _Eptr, idx)`, donde `_Eptr` es un objeto interno de la función. Si `str.c_str() == *_Eptr`, lanza un objeto de tipo `invalid_argument`. Si esa llamada, al ejecutarse, establecería `errno`, lanza un objeto de tipo `out_of_range`. De lo contrario, si *IDX* no es un puntero nulo, la función almacena `*_Eptr -  str.c_str()` en `*idx` y devuelve el valor.

## <a name="stoul"></a><a name="stoul"></a>  stoul

Convierte una secuencia de caracteres en un entero largo sin signo.

```cpp
unsigned long stoul(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long stoul(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parámetros

\ *Str*
La secuencia de caracteres que se convertirá.

\ *IDX*
El valor del índice del primer carácter que no se convertirá.

*base*\
La base numérica que se usará.

### <a name="return-value"></a>Valor devuelto

El valor del entero largo sin signo.

### <a name="remarks"></a>Observaciones

La función convierte la secuencia de elementos de *Str* en un valor de tipo **`unsigned long`** como si se llamara a `strtoul( str.c_str(), _Eptr, idx)`, donde `_Eptr` es un objeto interno de la función. Si `str.c_str() == *_Eptr`, lanza un objeto de tipo `invalid_argument`. Si esa llamada, al ejecutarse, establecería `errno`, lanza un objeto de tipo `out_of_range`. De lo contrario, si *IDX* no es un puntero nulo, la función almacena `*_Eptr -  str.c_str()` en `*idx` y devuelve el valor.

## <a name="stoull"></a><a name="stoull"></a>  stoull

Convierte una secuencia de caracteres en una **`unsigned long long`** .

```cpp
unsigned long long stoull(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long long stoull(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parámetros

\ *Str*
La secuencia de caracteres que se convertirá.

\ *IDX*
El valor del índice del primer carácter que no se convertirá.

*base*\
La base numérica que se usará.

### <a name="return-value"></a>Valor devuelto

Valor de **`unsigned long long`** .

### <a name="remarks"></a>Observaciones

La función convierte la secuencia de elementos de *Str* en un valor de tipo **`unsigned long long`** como si se llamara a `strtoull( str.c_str(), _Eptr, idx)`, donde `_Eptr` es un objeto interno de la función. Si `str.c_str() == *_Eptr`, lanza un objeto de tipo `invalid_argument`. Si esa llamada, al ejecutarse, establecería `errno`, lanza un objeto de tipo `out_of_range`. De lo contrario, si *IDX* no es un puntero nulo, la función almacena `*_Eptr -  str.c_str()` en `*idx` y devuelve el valor.

## <a name="swap"></a><a name="swap"></a> swap

Intercambia las matrices de caracteres de dos cadenas.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Una cadena cuyos elementos se van a intercambiar con los elementos de otra cadena.

\ *derecha*
La otra cadena, cuyos elementos se deben intercambiar con los de la primera cadena.

### <a name="remarks"></a>Observaciones

La función de plantilla ejecuta la función miembro especializada *.* [swap](../standard-library/basic-string-class.md#swap)(*right*) para las cadenas, lo que garantiza una complejidad constante.

### <a name="example"></a>Ejemplo

```cpp
// string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   swap ( s1 , s2 );
   cout << "\nAfter swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.

After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="to_string"></a><a name="to_string"></a>  to_string

Convierte un valor en `string`.

```cpp
string to_string(int value);
string to_string(unsigned int value);
string to_string(long value);
string to_string(unsigned long value);
string to_string(long long value);
string to_string(unsigned long long value);
string to_string(float value);
string to_string(double value);
string to_string(long double value);
```

### <a name="parameters"></a>Parámetros

*value*\
El valor que se va a convertir.

### <a name="return-value"></a>Valor devuelto

`string` que representa el valor.

### <a name="remarks"></a>Observaciones

La función convierte el *valor* en una secuencia de elementos almacenados en un objeto de matriz `Buf` interna a la función como si se llamara a `sprintf(Buf, Fmt, value)`, donde `Fmt` es.

- `"%d"` si el *valor* es de tipo **`int`**

- `"%u"` si el *valor* es de tipo **`unsigned int`**

- `"%ld"` si el *valor* es de tipo **`long`**

- `"%lu"` si el *valor* es de tipo **`unsigned long`**

- `"%lld"` si el *valor* es de tipo **`long long`**

- `"%llu"` si el *valor* es de tipo **`unsigned long long`**

- `"%f"` si el *valor* es de tipo **`float`** o **`double`**

- `"%Lf"` si el *valor* es de tipo **`long double`**

La función devuelve `string(Buf)`.

## <a name="to_wstring"></a><a name="to_wstring"></a>  to_wstring

Convierte un valor en una cadena de tipo ancho.

```cpp
wstring to_wstring(int value);
wstring to_wstring(unsigned int value);
wstring to_wstring(long value);
wstring to_wstring(unsigned long value);
wstring to_wstring(long long value);
wstring to_wstring(unsigned long long value);
wstring to_wstring(float value);
wstring to_wstring(double value);
wstring to_wstring(long double value);
```

### <a name="parameters"></a>Parámetros

*value*\
El valor que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Cadena de tipo ancho que representa el valor.

### <a name="remarks"></a>Observaciones

La función convierte el *valor* en una secuencia de elementos almacenados en un objeto de matriz `Buf` interna a la función como si se llamara a `swprintf(Buf, Len, Fmt, value)`, donde `Fmt` es.

- `L"%d"` si el *valor* es de tipo **`int`**

- `L"%u"` si el *valor* es de tipo **`unsigned int`**

- `L"%ld"` si el *valor* es de tipo **`long`**

- `L"%lu"` si el *valor* es de tipo **`unsigned long`**

- `L"%lld"` si el *valor* es de tipo **`long long`**

- `L"%llu"` si el *valor* es de tipo **`unsigned long long`**

- `L"%f"` si el *valor* es de tipo **`float`** o **`double`**

- `L"%Lf"` si el *valor* es de tipo **`long double`**

La función devuelve `wstring(Buf)`.

## <a name="see-also"></a>Consulte también

[\<string>](../standard-library/string.md)
