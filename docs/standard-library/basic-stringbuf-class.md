---
title: basic_stringbuf (Clase)
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringbuf
- sstream/std::basic_stringbuf::allocator_type
- sstream/std::basic_stringbuf::char_type
- sstream/std::basic_stringbuf::int_type
- sstream/std::basic_stringbuf::off_type
- sstream/std::basic_stringbuf::pos_type
- sstream/std::basic_stringbuf::traits_type
- sstream/std::basic_stringbuf::overflow
- sstream/std::basic_stringbuf::pbackfail
- sstream/std::basic_stringbuf::seekoff
- sstream/std::basic_stringbuf::seekpos
- sstream/std::basic_stringbuf::str
- sstream/std::basic_stringbuf::underflow
helpviewer_keywords:
- std::basic_stringbuf [C++]
- std::basic_stringbuf [C++], allocator_type
- std::basic_stringbuf [C++], char_type
- std::basic_stringbuf [C++], int_type
- std::basic_stringbuf [C++], off_type
- std::basic_stringbuf [C++], pos_type
- std::basic_stringbuf [C++], traits_type
- std::basic_stringbuf [C++], overflow
- std::basic_stringbuf [C++], pbackfail
- std::basic_stringbuf [C++], seekoff
- std::basic_stringbuf [C++], seekpos
- std::basic_stringbuf [C++], str
- std::basic_stringbuf [C++], underflow
ms.assetid: 40c85f9e-42a5-4a65-af5c-23c8e3bf8113
ms.openlocfilehash: 0445c2f8868fc9f2863ad4a2a12cc00261546c75
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447842"
---
# <a name="basicstringbuf-class"></a>basic_stringbuf (Clase)

Describe un búfer de secuencia que controla la transmisión bidireccional entre elementos de tipo `Elem` —cuyos rasgos de caracteres están determinados por la clase `Tr`— y una secuencia de elementos almacenados en un objeto Array.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

*Alloc*\
Clase de asignador.

*Elem*\
Tipo de elemento básico de la cadena.

*Anticipo*\
Rasgos de caracteres especializados en el elemento básico de la cadena.

## <a name="remarks"></a>Comentarios

El objeto está asignado, extendido y liberado según sea necesario para dar cabida a los cambios en la secuencia.

Un objeto de clase basic_stringbuf< `Elem`, `Tr`, `Alloc`> almacena una copia del argumento `ios_base::`[openmode](../standard-library/ios-base-class.md#openmode) de su constructor como su modo `stringbuf` **mode**:

- Si `mode & ios_base::in` es distinto de cero, el búfer de entrada es accesible. Para obtener más información, vea [basic_streambuf (Clase)](../standard-library/basic-streambuf-class.md).

- Si `mode & ios_base::out` es distinto de cero, el búfer de salida es accesible.

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|Construye un objeto de tipo `basic_stringbuf`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|DESCRIPCIÓN|
|-|-|
|[allocator_type](#allocator_type)|El tipo es un sinónimo del parámetro de plantilla *Alloc*.|
|[char_type](#char_type)|Asocia un nombre de tipo al parámetro de plantilla *Elem*.|
|[int_type](#int_type)|Convierte este tipo dentro `basic_filebuf`del ámbito de su equivalente al tipo del mismo nombre en el ámbito *TR* .|
|[off_type](#off_type)|Convierte este tipo dentro `basic_filebuf`del ámbito de su equivalente al tipo del mismo nombre en el ámbito *TR* .|
|[pos_type](#pos_type)|Convierte este tipo dentro `basic_filebuf`del ámbito de su equivalente al tipo del mismo nombre en el ámbito *TR* .|
|[traits_type](#traits_type)|Asocia un nombre de tipo al parámetro de plantilla *Tr*.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[overflow](#overflow)|Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.|
|[pbackfail](#pbackfail)|La función miembro virtual protegida trata de colocar un elemento en el búfer de entrada y, después, convertirlo en el elemento actual (indicado por el siguiente puntero).|
|[seekoff](#seekoff)|La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.|
|[seekpos](#seekpos)|La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.|
|[str](#str)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|
|swap||
|[underflow](#underflow)|Función miembro virtual protegida que extrae el elemento actual de la secuencia de entrada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<sstream>

**Espacio de nombres:** std

## <a name="allocator_type"></a>  basic_stringbuf::allocator_type

El tipo es un sinónimo del parámetro de plantilla *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbuf"></a>  basic_stringbuf::basic_stringbuf

Construye un objeto de tipo `basic_stringbuf`.

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Mode*\
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*CAD*\
Un objeto de tipo [basic_string](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Comentarios

El primer constructor almacena un puntero nulo en todos los punteros que controlan el búfer de entrada y el de salida. Para obtener más información, vea la sección Comentarios del tema [basic_streambuf (Clase)](../standard-library/basic-streambuf-class.md). También almacena *_Mode* como el modo stringbuf. Para obtener más información, vea la sección Comentarios del tema [basic_stringbuf (Clase)](../standard-library/basic-stringbuf-class.md).

El segundo constructor asigna una copia de la secuencia controlada por el objeto de cadena *Str*. Si `_Mode & ios_base::in` es distinto de cero, establece el búfer de entrada para que comience a leer al inicio de la secuencia. Si `_Mode & ios_base::out` es distinto de cero, establece el búfer de salida para que comience a escribir al inicio de la secuencia. También almacena *_Mode* como el modo stringbuf. Para obtener más información, vea la sección Comentarios del tema [basic_stringbuf (Clase)](../standard-library/basic-stringbuf-class.md).

## <a name="char_type"></a>  basic_stringbuf::char_type

Asocia un nombre de tipo al parámetro de plantilla *Elem*.

```cpp
typedef Elem char_type;
```

## <a name="int_type"></a>  basic_stringbuf::int_type

Convierte este tipo en el ámbito de basic_filebuf's equivalente al tipo del mismo nombre en el `Tr` ámbito.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_stringbuf::off_type

Convierte este tipo en el ámbito de basic_filebuf's equivalente al tipo del mismo nombre en el `Tr` ámbito.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="overflow"></a>  basic_stringbuf::overflow

Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parámetros

*_Meta*\
El carácter que se va a insertar en el búfer o `traits_type::eof`.

### <a name="return-value"></a>Valor devuelto

Si la función no se ejecuta correctamente, devuelve `traits_type::eof`. De lo contrario, devuelve **traits_type::** [not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Comentarios

*Si\_meta* no es igual a **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), la función miembro virtual protegida intenta insertar el elemento **traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( *\_meta*) en el búfer de salida. Puede hacerlo de varias maneras:

- Si está disponible una posición de escritura, puede almacenar el elemento en la posición de escritura e incrementar el puntero siguiente para el búfer de salida.

- Puede proporcionar una posición de escritura al asignar almacenamiento nuevo o adicional para el búfer de salida. Extender el búfer de salida de esta forma también extiende cualquier búfer de entrada asociado.

## <a name="pbackfail"></a>  basic_stringbuf::pbackfail

La función miembro virtual protegida intenta devolver un elemento al búfer de entrada y después convertirlo en el elemento actual (indicado por el siguiente puntero).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parámetros

*_Meta*\
El carácter que se va a insertar en el búfer o `traits_type::eof`.

### <a name="return-value"></a>Valor devuelto

Si la función no se ejecuta correctamente, devuelve `traits_type::eof`. De lo contrario, devuelve **traits_type::** [not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Comentarios

Si *_Meta* compara igual a **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), el elemento que se va a devolver es realmente el que ya está en la secuencia antes del elemento actual. De lo contrario, ese elemento se sustituye por **bytes** = **traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)(_ *Meta*). La función puede devolver un elemento de distintas maneras:

- Si está disponible una posición de devolución y el elemento almacenado es igual a byte, puede disminuir el puntero siguiente para el búfer de entrada.

- Si está disponible una posición de devolución y si el modo de stringbuf permite que la secuencia se modifique (**mode & ios_base::out** es distinto de cero), puede almacenar byte en la posición de devolución y disminuir el puntero siguiente para el búfer de entrada.

## <a name="pos_type"></a>  basic_stringbuf::pos_type

Convierte este tipo en el ámbito de basic_filebuf's equivalente al tipo del mismo nombre en el `Tr` ámbito.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_stringbuf::seekoff

La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Off*\
Posición que se va a buscar en relación con *_Way*. Para obtener más información, vea [basic_stringbuf::off_type](#off_type).

*_Way*\
El punto de partida de las operaciones de desplazamiento. Vea los valores posibles en [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir).

*_Mode*\
Especifica el modo de la posición del puntero. El valor predeterminado es permitirle modificar las posiciones de lectura y escritura. Para obtener más información, vea [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Valor devuelto

Devuelve la posición nueva o una posición de flujo no válida.

### <a name="remarks"></a>Comentarios

Para un objeto de la clase `basic_stringbuf<Elem, Tr, Alloc>`, una posición de flujo consta solo de un desplazamiento de flujo. El desplazamiento cero designa el primer elemento de la secuencia controlada.

La nueva posición se determina de la siguiente forma:

- Si `_Way` es == ,la nueva posición es el principio del flujo más *_Off.* `ios_base::beg`

- Si `_Way` es == ,la nueva posición es la posición de la secuencia actual más *_Off.* `ios_base::cur`

- Si `_Way` es == ,la nueva posición es el final de la secuencia más *_Off.* `ios_base::end`

Si `_Mode & ios_base::in` es distinto de cero, la función modifica la siguiente posición de lectura en el búfer de entrada. Si `_Mode & ios_base::out` es distinto de cero, la función modifica la siguiente posición de escritura en el búfer de salida. Para que un flujo se vea afectado, debe existir su búfer. Para que una operación de posicionamiento se realice correctamente, la posición del flujo resultante debe encontrarse dentro de la secuencia controlada. Si la función afecta a ambas posiciones de flujo, *_Way* `ios_base::beg` debe `ios_base::end` ser o y ambos flujos se colocan en el mismo elemento. En caso contrario (o si no se ve afectada ninguna posición), se produce un error en la operación de posicionamiento.

Si la función modifica correctamente una o las dos posiciones del flujo, devuelve la posición del flujo resultante. De lo contrario, se produce un error y devuelve una posición de flujo no válida.

## <a name="seekpos"></a>  basic_stringbuf::seekpos

La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Sp*\
La posición que se va a buscar.

*_Mode*\
Especifica el modo de la posición del puntero. El valor predeterminado es permitirle modificar las posiciones de lectura y escritura.

### <a name="return-value"></a>Valor devuelto

Si la función modifica correctamente una o las dos posiciones del flujo, devuelve la posición del flujo resultante. De lo contrario, se produce un error y devuelve una posición de flujo no válida. Para determinar si la posición del flujo no es válida, compare el valor devuelto con `pos_type(off_type(-1))`.

### <a name="remarks"></a>Comentarios

Para un objeto de la clase basic_stringbuf< **Elem**, **Tr**, `Alloc`>, una posición de flujo consta solo de un desplazamiento de flujo. El desplazamiento cero designa el primer elemento de la secuencia controlada. La nueva posición se determina mediante _ *Sp*.

Si **mode & ios_base::in** es distinto de cero, la función modifica la siguiente posición de lectura en el búfer de entrada. Si **mode & ios_base::out** es distinto de cero, la función modifica la siguiente posición de escritura en el búfer de salida. Para que un flujo se vea afectado, debe existir su búfer. Para que una operación de posicionamiento se realice correctamente, la posición del flujo resultante debe encontrarse dentro de la secuencia controlada. En caso contrario (o si no se ve afectada ninguna posición), se produce un error en la operación de posicionamiento.

## <a name="str"></a>  basic_stringbuf::str

Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parámetros

*_Newstr*\
La nueva cadena.

### <a name="return-value"></a>Valor devuelto

Devuelve un objeto de clase [basic_string](../standard-library/basic-string-class.md)\< **Elem**, **Tr**, Alloc **>,** cuya secuencia controlada es una copia de la secuencia controlada por **\*this**.

### <a name="remarks"></a>Comentarios

El primer miembro de la función devuelve un objeto de clase basic_string< **Elem**, **Tr**, `Alloc`>, cuya secuencia controlada es una copia de la secuencia controlada por **\*this**. La secuencia copiada depende del modo de stringbuf almacenado:

- Si **mode & ios_base::out** es distinto de cero y existe un búfer de salida, la secuencia es el búfer de salida completo (elementos [epptr](../standard-library/basic-streambuf-class.md#epptr) - [pbase](../standard-library/basic-streambuf-class.md#pbase) que empiezan por `pbase`).

- Si **mode & ios_base::in** es distinto de cero y existe un búfer de entrada, la secuencia es el búfer de entrada completo (elementos [egptr](../standard-library/basic-streambuf-class.md#egptr) - [eback](../standard-library/basic-streambuf-class.md#eback) que empiezan por `eback`).

- De lo contrario, la secuencia copiada está vacía.

La segunda función miembro desasigna cualquier secuencia controlada actualmente por **\*this**. A continuación, asigna una copia de la secuencia controlada por *_Newstr*. Si **mode & ios_base::in** es distinto de cero, establece el búfer de entrada para que comience a leer al inicio de la secuencia. Si **mode & ios_base::out** es distinto de cero, establece el búfer de salida para que comience a escribir al inicio de la secuencia.

### <a name="example"></a>Ejemplo

```cpp
// basic_stringbuf_str.cpp
// compile with: /EHsc
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   basic_string<char> i( "test" );
   stringstream ss;

   ss.rdbuf( )->str( i );
   cout << ss.str( ) << endl;

   ss << "z";
   cout << ss.str( ) << endl;

   ss.rdbuf( )->str( "be" );
   cout << ss.str( ) << endl;
}
```

```Output
test
zest
be
```

## <a name="traits_type"></a>  basic_stringbuf::traits_type

Asocia un nombre de tipo al parámetro de plantilla *Tr*.

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla *Tr*.

## <a name="underflow"></a>  basic_stringbuf::underflow

Función virtual protegida que extrae el elemento actual de la secuencia de entrada.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Valor devuelto

Si la función no se puede ejecutar correctamente, devuelve **traits_type::** [eof](../standard-library/char-traits-struct.md#eof). De lo contrario, devuelve el elemento actual en el flujo de entrada, que está convertido.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida `byte` intenta extraer el elemento actual del búfer de entrada, avanzar la posición de la secuencia actual y devolver el elemento como **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **byte**). Puede hacerlo de una manera: Si hay una posición de lectura disponible, toma `byte` como el elemento almacenado en la posición de lectura y avanza el puntero siguiente para el búfer de entrada.

## <a name="swap"></a>  basic_streambuf::swap

Intercambia el contenido de este búfer de cadena con otro búfer de cadena.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Parámetros

*distinta*\
El parámetro basic_stringbuf cuyo contenido se intercambiará con este basic_stringbuf.

### <a name="remarks"></a>Comentarios

## <a name="op_eq"></a>  basic_stringbuf::operator=

Asigna el contenido del basic_stringbuf del lado derecho del operador al basic_stringbuf del lado izquierdo.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Parámetros

*distinta*\
Un basic_stringbuf cuyo contenido, incluidas las características de configuración regional, se asignará al stringbuf del lado izquierdo del operador.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
