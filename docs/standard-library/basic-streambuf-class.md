---
title: basic_streambuf (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- streambuf/std::basic_streambuf
- streambuf/std::basic_streambuf::char_type
- streambuf/std::basic_streambuf::int_type
- streambuf/std::basic_streambuf::off_type
- streambuf/std::basic_streambuf::pos_type
- streambuf/std::basic_streambuf::traits_type
- streambuf/std::basic_streambuf::eback
- streambuf/std::basic_streambuf::egptr
- streambuf/std::basic_streambuf::epptr
- streambuf/std::basic_streambuf::gbump
- streambuf/std::basic_streambuf::getloc
- streambuf/std::basic_streambuf::gptr
- streambuf/std::basic_streambuf::imbue
- streambuf/std::basic_streambuf::in_avail
- streambuf/std::basic_streambuf::overflow
- streambuf/std::basic_streambuf::pbackfail
- streambuf/std::basic_streambuf::pbase
- streambuf/std::basic_streambuf::pbump
- streambuf/std::basic_streambuf::pptr
- streambuf/std::basic_streambuf::pubimbue
- streambuf/std::basic_streambuf::pubseekoff
- streambuf/std::basic_streambuf::pubseekpos
- streambuf/std::basic_streambuf::pubsetbuf
- streambuf/std::basic_streambuf::pubsync
- streambuf/std::basic_streambuf::sbumpc
- streambuf/std::basic_streambuf::seekoff
- streambuf/std::basic_streambuf::seekpos
- streambuf/std::basic_streambuf::setbuf
- streambuf/std::basic_streambuf::setg
- streambuf/std::basic_streambuf::setp
- streambuf/std::basic_streambuf::sgetc
- streambuf/std::basic_streambuf::sgetn
- streambuf/std::basic_streambuf::showmanyc
- streambuf/std::basic_streambuf::snextc
- streambuf/std::basic_streambuf::sputbackc
- streambuf/std::basic_streambuf::sputc
- streambuf/std::basic_streambuf::sputn
- streambuf/std::basic_streambuf::stossc
- streambuf/std::basic_streambuf::sungetc
- streambuf/std::basic_streambuf::swap
- streambuf/std::basic_streambuf::sync
- streambuf/std::basic_streambuf::uflow
- streambuf/std::basic_streambuf::underflow
- streambuf/std::basic_streambuf::xsgetn
- streambuf/std::basic_streambuf::xsputn
dev_langs:
- C++
helpviewer_keywords:
- std::basic_streambuf [C++]
- std::basic_streambuf [C++], char_type
- std::basic_streambuf [C++], int_type
- std::basic_streambuf [C++], off_type
- std::basic_streambuf [C++], pos_type
- std::basic_streambuf [C++], traits_type
- std::basic_streambuf [C++], eback
- std::basic_streambuf [C++], egptr
- std::basic_streambuf [C++], epptr
- std::basic_streambuf [C++], gbump
- std::basic_streambuf [C++], getloc
- std::basic_streambuf [C++], gptr
- std::basic_streambuf [C++], imbue
- std::basic_streambuf [C++], in_avail
- std::basic_streambuf [C++], overflow
- std::basic_streambuf [C++], pbackfail
- std::basic_streambuf [C++], pbase
- std::basic_streambuf [C++], pbump
- std::basic_streambuf [C++], pptr
- std::basic_streambuf [C++], pubimbue
- std::basic_streambuf [C++], pubseekoff
- std::basic_streambuf [C++], pubseekpos
- std::basic_streambuf [C++], pubsetbuf
- std::basic_streambuf [C++], pubsync
- std::basic_streambuf [C++], sbumpc
- std::basic_streambuf [C++], seekoff
- std::basic_streambuf [C++], seekpos
- std::basic_streambuf [C++], setbuf
- std::basic_streambuf [C++], setg
- std::basic_streambuf [C++], setp
- std::basic_streambuf [C++], sgetc
- std::basic_streambuf [C++], sgetn
- std::basic_streambuf [C++], showmanyc
- std::basic_streambuf [C++], snextc
- std::basic_streambuf [C++], sputbackc
- std::basic_streambuf [C++], sputc
- std::basic_streambuf [C++], sputn
- std::basic_streambuf [C++], stossc
- std::basic_streambuf [C++], sungetc
- std::basic_streambuf [C++], swap
- std::basic_streambuf [C++], sync
- std::basic_streambuf [C++], uflow
- std::basic_streambuf [C++], underflow
- std::basic_streambuf [C++], xsgetn
- std::basic_streambuf [C++], xsputn
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ab94a9aadc40b4313995a71171d6712657e7ff0
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964959"
---
# <a name="basicstreambuf-class"></a>basic_streambuf (Clase)

Describe una clase base abstracta para derivar un búfer de secuencia, que controla la transmisión de elementos a y desde una representación concreta de una secuencia.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>Parámetros

*Elem* A [char_type](#char_type).

*TR* el carácter [traits_type](#traits_type).

## <a name="remarks"></a>Comentarios

La clase de plantilla describe una clase base abstracta para derivar un búfer de secuencia, que controla la transmisión de elementos a y desde una representación concreta de una secuencia. Un objeto de clase `basic_streambuf` ayuda a controlar un flujo con elementos de tipo *Tr*, también conocida como [char_type](#char_type), cuyos rasgos de caracteres están determinados por la clase [char_traits](../standard-library/char-traits-struct.md), también conocida como [traits_type](#traits_type).

Cada búfer de secuencia controla conceptualmente dos secuencias independientes: una para extracciones (entrada) y otra para inserciones (salida). Pero una representación específica podría hacer inaccesible una de estas secuencias o las dos. Normalmente mantiene cierta relación entre las dos secuencias. Lo que se inserta en el flujo de salida de un objeto [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`>, por ejemplo, es lo que más adelante se extraerá de su flujo de entrada. Al colocar un flujo de un objeto [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, se coloca el otro flujo en tándem.

La interfaz pública a la clase de plantilla `basic_streambuf` proporciona las operaciones comunes a todos los búferes de secuencia, independientemente de lo especializados que sean. La interfaz protegida proporciona las operaciones necesarias para que una representación específica de una secuencia haga su trabajo. Las funciones miembro virtuales protegidas le permiten personalizar el comportamiento de un búfer de secuencia derivado para una representación específica de una secuencia. Cada búfer de secuencia derivado de esta biblioteca describe cómo especializa el comportamiento de sus funciones miembro virtuales protegidas. El comportamiento predeterminado de la clase base, que a menudo consiste en no hacer nada, se describe en este tema.

Las restantes funciones miembro protegidas controlan las operaciones de copia a y desde cualquier almacenamiento proporcionado para almacenar en búfer las transmisiones a y desde secuencias. Por ejemplo, un búfer de entrada se caracteriza por:

- [eback](#eback), un puntero al principio del búfer.

- [gptr](#gptr), un puntero al siguiente elemento que se va a leer.

- [egptr](#egptr), un puntero inmediatamente después del final del búfer.

De forma similar, un búfer de salida se caracteriza por:

- [pbase](#pbase), un puntero al principio del búfer.

- [pptr](#pptr), un puntero al siguiente elemento que se va a escribir.

- [epptr](#epptr), un puntero inmediatamente después del final del búfer.

Para cualquier búfer, se usa el siguiente protocolo:

- Si el siguiente puntero es nulo, no existe ningún búfer. De lo contrario, los tres punteros apuntan a la misma secuencia. Se puede comparar su orden de forma segura.

- En el caso de un búfer de salida, si el siguiente puntero tiene, en comparación, un valor menor que el puntero final, puede almacenar un elemento en la posición de escritura designada por el siguiente puntero.

- En el caso de un búfer de entrada, si el siguiente puntero tiene, en comparación, un valor menor que el puntero final, puede leer un elemento en la posición de lectura designada por el siguiente puntero.

- En el caso de un búfer de entrada, si el puntero inicial tiene, en comparación, un valor menor que el siguiente puntero, puede devolver un elemento a la posición de devolución designada por el siguiente puntero reducido.

Todas las funciones miembro virtuales protegidas que escriba para una clase derivada de `basic_streambuf`< `Elem`, `Tr`> deben cooperar en el mantenimiento de este protocolo.

Un objeto de clase `basic_streambuf`< `Elem`, `Tr`> almacena los seis punteros descritos anteriormente. También almacena un objeto de configuración regional en un objeto de tipo [locale](../standard-library/locale-class.md) para su uso potencial por parte de un búfer de flujo derivado.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_streambuf](#basic_streambuf)|Construye un objeto de tipo `basic_streambuf`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[char_type](#char_type)|Asocia un nombre de tipo con el parámetro de plantilla `Elem`.|
|[int_type](#int_type)|Asocia un nombre de tipo dentro del ámbito `basic_streambuf` con el parámetro de plantilla `Elem`.|
|[off_type](#off_type)|Asocia un nombre de tipo dentro del ámbito `basic_streambuf` con el parámetro de plantilla `Elem`.|
|[pos_type](#pos_type)|Asocia un nombre de tipo dentro del ámbito `basic_streambuf` con el parámetro de plantilla `Elem`.|
|[traits_type](#traits_type)|Asocia un nombre de tipo con el parámetro de plantilla `Tr`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[eback](#eback)|Función protegida que devuelve un puntero al principio del búfer de entrada.|
|[egptr](#egptr)|Función protegida que devuelve un puntero justo después del final del búfer de entrada.|
|[epptr](#epptr)|Función protegida que devuelve un puntero justo después del final del búfer de salida.|
|[gbump](#gbump)|Función protegida que agrega `count` al siguiente puntero del búfer de entrada.|
|[getloc](#getloc)|Obtiene la configuración regional del objeto `basic_streambuf`.|
|[gptr](#gptr)|Función protegida que devuelve un puntero al siguiente elemento del búfer de entrada.|
|[imbue](#imbue)|Función virtual protegida a la que llama [pubimbue](#pubimbue).|
|[in_avail](#in_avail)|Devuelve el número de elementos que están listos para ser leídos desde el búfer.|
|[overflow](#overflow)|Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.|
|[pbackfail](#pbackfail)|Función miembro virtual protegida que intenta volver a colocar un elemento en el flujo de entrada y convertirlo después en el elemento actual (indicado por el puntero siguiente).|
|[pbase](#pbase)|Función protegida que devuelve un puntero al principio del búfer de salida.|
|[pbump](#pbump)|Función protegida que agrega `count` al siguiente puntero del búfer de salida.|
|[pptr](#pptr)|Función protegida que devuelve un puntero al siguiente elemento del búfer de salida.|
|[pubimbue](#pubimbue)|Establece la configuración regional del objeto `basic_streambuf`.|
|[pubseekoff](#pubseekoff)|Llama a [seekoff](#seekoff), una función virtual protegida que se invalida en una clase derivada.|
|[pubseekpos](#pubseekpos)|Llama a [seekpos](#seekpos), una función virtual protegida que se invalida en una clase derivada, y restablece la posición actual del puntero.|
|[pubsetbuf](#pubsetbuf)|Llama a [setbuf](#setbuf), una función virtual protegida que se invalida en una clase derivada.|
|[pubsync](#pubsync)|Llama a [sync](#sync), una función virtual protegida que se invalida en una clase derivada, y actualiza el flujo externo asociado a este búfer.|
|[sbumpc](#sbumpc)|Lee y devuelve el elemento actual, moviendo el puntero de la secuencia.|
|[seekoff](#seekoff)|La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.|
|[seekpos](#seekpos)|La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas.|
|[setbuf](#setbuf)|La función miembro virtual protegida realiza una determinada operación para cada búfer de secuencia derivado.|
|[setg](#setg)|Función protegida que almacena `_Gbeg` en el puntero inicial, `_Gnext` en el siguiente puntero y `_Gend` en el puntero final del búfer de entrada.|
|[setp](#setp)|Función protegida que almacena `_Pbeg` en el puntero inicial y `_Pend` en el puntero final del búfer de salida.|
|[sgetc](#sgetc)|Devuelve el elemento actual sin cambiar la posición en la secuencia.|
|[sgetn](#sgetn)|Devuelve el número de elementos leídos.|
|[showmanyc](#showmanyc)|Función miembro virtual protegida que devuelve el recuento del número de caracteres que se puede extraer del flujo de entrada y se asegura de que el programa no estará sujeto a una espera indefinida.|
|[snextc](#snextc)|Lee el elemento actual y devuelve el siguiente elemento.|
|[sputbackc](#sputbackc)|Coloca un `char_type` en la secuencia.|
|[sputc](#sputc)|Coloca un carácter en la secuencia.|
|[sputn](#sputn)|Coloca una cadena de caracteres en la secuencia.|
|[stossc](#stossc)|Mueve más allá del elemento actual de la secuencia.|
|[sungetc](#sungetc)|Obtiene un carácter de la secuencia.|
|[swap](#swap)|Intercambia los valores de este objeto por los valores en el parámetro del objeto `basic_streambuf` proporcionado.|
|[sync](#sync)|Función virtual protegida que intenta sincronizar las secuencias controladas con cualquier secuencia externa asociada.|
|[uflow](#uflow)|Función virtual protegida que extrae el elemento actual del flujo de entrada.|
|[underflow](#underflow)|Función virtual protegida que extrae el elemento actual del flujo de entrada.|
|[xsgetn](#xsgetn)|Función virtual protegida que extrae elementos del flujo de entrada.|
|[xsputn](#xsputn)|Función virtual protegida que inserta elementos en el flujo de salida.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator=](#op_eq)|Asigna los valores de este objeto desde otro objeto `basic_streambuf`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<streambuf>

**Espacio de nombres:** std

## <a name="basic_streambuf"></a>  basic_streambuf::basic_streambuf

Construye un objeto de tipo `basic_streambuf`.

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>Parámetros

*derecha* referencia lvalue a la `basic_streambuf` objeto que se usa para establecer los valores para este `basic_streambuf` objeto.

### <a name="remarks"></a>Comentarios

El primer constructor protegido almacena un puntero nulo en todos los punteros que controlan el búfer de entrada y el de salida. También almacena `locale::classic` en el objeto de configuración regional. Para más información, vea [locale::classic](../standard-library/locale-class.md#classic).

El segundo constructor protegido copia los punteros y la configuración regional de *derecho*.

## <a name="char_type"></a>  basic_streambuf::char_type

Asocia un nombre de tipo al parámetro de plantilla **Elem**.

```cpp
typedef Elem char_type;
```

## <a name="eback"></a>  basic_streambuf::eback

Función protegida que devuelve un puntero al principio del búfer de entrada.

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al principio del búfer de entrada.

## <a name="egptr"></a>  basic_streambuf::egptr

Función protegida que devuelve un puntero justo después del final del búfer de entrada.

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero inmediatamente después del final del búfer de entrada.

## <a name="epptr"></a>  basic_streambuf::epptr

Función protegida que devuelve un puntero justo después del final del búfer de salida.

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero inmediatamente después del final del búfer de salida.

## <a name="gbump"></a>  basic_streambuf::gbump

Función protegida que agrega *recuento* al siguiente puntero del búfer de entrada.

```cpp
void gbump(int count);
```

### <a name="parameters"></a>Parámetros

*recuento* cantidad por la que se va a hacer avanzar el puntero.

## <a name="getloc"></a>  basic_streambuf::getloc

Obtiene la configuración regional del objeto basic_streambuf.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto de configuración regional almacenado.

### <a name="remarks"></a>Comentarios

Para obtener información relacionada, vea [ios_base::getloc](../standard-library/ios-base-class.md#getloc).

### <a name="example"></a>Ejemplo

```cpp
// basic_streambuf_getloc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << cout.rdbuf( )->getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="gptr"></a>  basic_streambuf::gptr

Función protegida que devuelve un puntero al siguiente elemento del búfer de entrada.

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al siguiente elemento del búfer de entrada.

## <a name="imbue"></a>  basic_streambuf::imbue

Función virtual protegida a la que llama [pubimbue](#pubimbue).

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parámetros

*_Loc* una referencia a una configuración regional.

### <a name="remarks"></a>Comentarios

El comportamiento predeterminado es no hacer nada.

## <a name="in_avail"></a>  basic_streambuf::in_avail

Devuelve el número de elementos que están listos para ser leídos desde el búfer.

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>Valor devuelto

Número de elementos que están listos para leerse desde el búfer.

### <a name="remarks"></a>Comentarios

Si un [posición de lectura](../standard-library/basic-streambuf-class.md) está disponible, la función miembro devuelve [egptr](#egptr) - [gptr](#gptr). De lo contrario, devuelve [showmanyc](#showmanyc).

### <a name="example"></a>Ejemplo

```cpp
// basic_streambuf_in_avail.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   char c;
   // cin's buffer is empty, in_avail will return 0
   cout << cin.rdbuf( )->in_avail( ) << endl;
   cin >> c;
   cout << cin.rdbuf( )->in_avail( ) << endl;
}
```

## <a name="int_type"></a>  basic_streambuf::int_type

Asocia un nombre de tipo del ámbito basic_streambuf a uno de los tipos de un parámetro de plantilla.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_streambuf::off_type

Asocia un nombre de tipo del ámbito basic_streambuf a uno de los tipos de un parámetro de plantilla.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_eq"></a>  basic_streambuf::operator=

Asigna los valores de este objeto desde otro objeto `basic_streambuf`.

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>Parámetros

*derecha* referencia lvalue a la `basic_streambuf` objeto que se usa para asignar valores a este objeto.

### <a name="remarks"></a>Comentarios

El operador de miembro protegido copia desde *derecho* los punteros que controlan el búfer de entrada y el búfer de salida. También almacena `right.`[getloc()](#getloc) en `locale object`. Devuelve `*this`.

## <a name="overflow"></a>  basic_streambuf::overflow

Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parámetros

*_Meta* el carácter que se va a insertar en el búfer, o **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Valor devuelto

Si la función no se ejecuta correctamente, devuelve **traits_type::eof** o inicia una excepción. De lo contrario, devuelve **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*). El comportamiento predeterminado es devolver **traits_type::eof**.

### <a name="remarks"></a>Comentarios

Si _ *Meta* no es igual a **traits_type::eof**, la función miembro virtual protegida intenta insertar el elemento **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) en el flujo de salida. Puede hacerlo de varias maneras:

- Si hay una `write position` disponible, puede almacenar el elemento en la posición de escritura e incrementar el puntero siguiente para el búfer de salida.

- Puede proporcionar una posición de escritura al asignar almacenamiento nuevo o adicional para el búfer de salida.

- Puede facilitar una posición de escritura al escribir en algún destino externo algunos o todos los elementos situados entre los punteros inicial y siguientes para el búfer de salida.

La función virtual overflow, junto con las funciones [sync](#sync) y [underflow](#underflow), define las características de la clase derivada de streambuf. Cada clase derivada podría implementar overflow de manera diferente, pero la interfaz con la clase stream que realiza la llamada es igual.

La función `overflow` recibe llamadas con más frecuencia de funciones públicas `streambuf` como `sputc` y `sputn` cuando el área de colocación está llena, pero otras clases, incluidas las clases stream, pueden llamar a `overflow` en cualquier momento.

La función usa los caracteres del área de colocación entre los punteros `pbase` y `pptr` y luego reinicializa el área de colocación. La función `overflow` también debe usar `nCh` (si `nCh` no es `EOF`) o puede optar por colocar ese carácter en la nueva área de colocación para que se use en la siguiente llamada.

La definición de usar varía entre clases derivadas. Por ejemplo, la clase `filebuf` escribe sus caracteres en un archivo, mientras que la clase `strstreambuf` los mantiene en su búfer y (si el búfer se designa como dinámico) lo expande en respuesta a una llamada a overflow. Esta expansión se logra al liberar el búfer antiguo y reemplazarlo por uno nuevo y mayor. Los punteros se ajustan según sea necesario.

## <a name="pbackfail"></a>  basic_streambuf::pbackfail

Función miembro virtual protegida que intenta volver a colocar un elemento en el flujo de entrada y convertirlo después en el elemento actual (indicado por el puntero siguiente).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parámetros

*_Meta* el carácter que se va a insertar en el búfer, o **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Valor devuelto

Si la función no se ejecuta correctamente, devuelve **traits_type::eof** o inicia una excepción. De lo contrario, devuelve algún otro valor. El comportamiento predeterminado es devolver **traits_type::eof**.

### <a name="remarks"></a>Comentarios

Si _ *Meta* es igual a **traits_type::eof**, el elemento que se va a devolver es realmente el que ya está en el flujo por delante del elemento actual. De lo contrario, ese elemento se sustituye por **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*). La función puede devolver un elemento de distintas maneras:

- Si hay una posición de devolución disponible, puede almacenar el elemento en ella y reducir el puntero siguiente para el búfer de entrada.

- Puede facilitar una posición de devolución al asignar almacenamiento nuevo o adicional para el búfer de entrada.

- En el caso de un búfer de flujo con flujos de entrada y salida comunes, puede facilitar una posición de devolución al escribir en algún destino externo algunos o todos los elementos situados entre los punteros inicial y siguientes para el búfer de salida.

## <a name="pbase"></a>  basic_streambuf::pbase

Función protegida que devuelve un puntero al principio del búfer de salida.

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al principio del búfer de salida.

## <a name="pbump"></a>  basic_streambuf::pbump

Función protegida que agrega *recuento* al siguiente puntero del búfer de salida.

```cpp
void pbump(int count);
```

### <a name="parameters"></a>Parámetros

*recuento de* el número de caracteres que se va a mover la escritura posición hacia delante.

## <a name="pos_type"></a>  basic_streambuf::pos_type

Asocia un nombre de tipo del ámbito basic_streambuf a uno de los tipos de un parámetro de plantilla.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="pptr"></a>  basic_streambuf::pptr

Función protegida que devuelve un puntero al siguiente elemento del búfer de salida.

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al siguiente elemento del búfer de salida.

## <a name="pubimbue"></a>  basic_streambuf::pubimbue

Establece la configuración regional del objeto basic_streambuf.

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>Parámetros

*_Loc* una referencia a una configuración regional.

### <a name="return-value"></a>Valor devuelto

Valor anterior almacenado en el objeto de configuración regional.

### <a name="remarks"></a>Comentarios

La función miembro almacena _ *Loc* en el objeto de configuración regional y llama a [imbue](#imbue).

### <a name="example"></a>Ejemplo

Vea [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) para obtener un ejemplo de uso de `pubimbue`.

## <a name="pubseekoff"></a>  basic_streambuf::pubseekoff

Llama a [seekoff](#seekoff), una función virtual protegida que se invalida en una clase derivada.

```cpp
pos_type pubseekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Off* buscar relativa a la posición *_Way*.

*_Way* el punto de partida para las operaciones de desplazamiento. Vea los valores posibles en [seekdir](../standard-library/ios-base-class.md#seekdir).

*_Which* especifica el modo de la posición del puntero. El valor predeterminado es permitirle modificar las posiciones de lectura y escritura.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición nueva o una posición de flujo no válida ([seekoff](#seekoff)(_ *Off*, `_Way`, `_Which`)).

### <a name="remarks"></a>Comentarios

Mueve el puntero en relación con *_Way*.

## <a name="pubseekpos"></a>  basic_streambuf::pubseekpos

Llama a [seekpos](#seekpos), una función virtual protegida que se invalida en una clase derivada, y restablece la posición actual del puntero.

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Sp* la posición para buscar.

*_Which* especifica el modo de la posición del puntero. El valor predeterminado es permitirle modificar las posiciones de lectura y escritura.

### <a name="return-value"></a>Valor devuelto

Posición nueva o una posición de flujo no válida. Para determinar si la posición del flujo no es válida, compare el valor devuelto con `pos_type(off_type(-1))`.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [seekpos](#seekpos)(_ *Sp*, `_Which`).

## <a name="pubsetbuf"></a>  basic_streambuf::pubsetbuf

Llama a [setbuf](#setbuf), una función virtual protegida que se invalida en una clase derivada.

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parámetros

*_Buffer* un puntero a `char_type` para esta instancia.

*recuento de* el tamaño del búfer.

### <a name="return-value"></a>Valor devuelto

Devuelve [setbuf](#setbuf)(`_Buffer`, `count`).

## <a name="pubsync"></a>  basic_streambuf::pubsync

Llama a [sync](#sync), una función virtual protegida que se invalida en una clase derivada, y actualiza el flujo externo asociado a este búfer.

```cpp
int pubsync();
```

### <a name="return-value"></a>Valor devuelto

Devuelve [sincronización](#sync) o -1 si un error.

## <a name="sbumpc"></a>  basic_streambuf::sbumpc

Lee y devuelve el elemento actual, moviendo el puntero de la secuencia.

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>Valor devuelto

Elemento actual.

### <a name="remarks"></a>Comentarios

Si hay una posición de lectura disponible, la función miembro devuelve **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)(**\***[gptr](#gptr)) e incrementa el puntero siguiente para el búfer de entrada. De lo contrario, devuelve [uflow](#uflow).

### <a name="example"></a>Ejemplo

```cpp
// basic_streambuf_sbumpc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->sbumpc( );
   cout << i << endl;
}
```

```Output

3

```

```Output

      33
51
```

## <a name="seekoff"></a>  basic_streambuf::seekoff

Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Off* buscar relativa a la posición *_Way*.

*_Way* el punto de partida para las operaciones de desplazamiento. Vea los valores posibles en [seekdir](../standard-library/ios-base-class.md#seekdir).

*_Which* especifica el modo de la posición del puntero. El valor predeterminado es permitirle modificar las posiciones de lectura y escritura.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición nueva o una posición de flujo no válida (`seekoff` (_ *Off*, `_Way`, `_Which`)).

### <a name="remarks"></a>Comentarios

La nueva posición se determina de la siguiente forma:

- Si `_Way` == `ios_base::beg`, la nueva posición es el principio del flujo más _ *Off*.

- Si `_Way` == `ios_base::cur`, la nueva posición es la posición actual del flujo más _ *Off*.

- Si `_Way` == `ios_base::end`, la nueva posición es el final del flujo más _ *Off*.

Normalmente, si **which & ios_base::in** es distinto de cero, el flujo de entrada se ve afectado y, si **which & ios_base::out** es distinto de cero, el flujo de salida se ve afectado. Pero el uso real de este parámetro varía entre búferes de flujo derivados.

Si la función consigue modificar la posición o posiciones de flujo correctamente, devuelve la posición de flujo resultante o una de las posiciones de flujo resultantes. De lo contrario, devuelve una posición de flujo no válida. El comportamiento predeterminado es devolver una posición de flujo no válida.

## <a name="seekpos"></a>  basic_streambuf::seekpos

Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Sp* la posición para buscar.

*_Which* especifica el modo de la posición del puntero. El valor predeterminado es permitirle modificar las posiciones de lectura y escritura.

### <a name="return-value"></a>Valor devuelto

Posición nueva o una posición de flujo no válida. Para determinar si la posición del flujo no es válida, compare el valor devuelto con `pos_type(off_type(-1))`.

### <a name="remarks"></a>Comentarios

La nueva posición es _ *Sp*.

Normalmente, si **which & ios_base::in** es distinto de cero, el flujo de entrada se ve afectado y, si **which & ios_base::out** es distinto de cero, el flujo de salida se ve afectado. Pero el uso real de este parámetro varía entre búferes de flujo derivados.

Si la función consigue modificar la posición o posiciones de flujo correctamente, devuelve la posición de flujo resultante o una de las posiciones de flujo resultantes. De lo contrario, devuelve una posición de flujo no válida (-1). El comportamiento predeterminado es devolver una posición de flujo no válida.

## <a name="setbuf"></a>  basic_streambuf::setbuf

Función miembro virtual protegida que realiza una operación específica de cada búfer de flujo derivado.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parámetros

*_Buffer* puntero a un búfer.

*recuento* tamaño del búfer.

### <a name="return-value"></a>Valor devuelto

El comportamiento predeterminado es devolver **this**.

### <a name="remarks"></a>Comentarios

Vea [basic_filebuf](../standard-library/basic-filebuf-class.md). `setbuf` proporciona un área de memoria para el objeto `streambuf` que se va a usar. En las clases derivadas se define cómo se va a usar el búfer.

## <a name="setg"></a>  basic_streambuf::setg

Función protegida que almacena _ *Gbeg* en el puntero inicial, `_Gnext` en el siguiente puntero y `_Gend` en el puntero final del búfer de entrada.

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>Parámetros

*_Gbeg* un puntero al principio del búfer.

*_Gnext* un puntero a cualquier ubicación en mitad del búfer.

*_Gend* un puntero al final del búfer.

## <a name="setp"></a>  basic_streambuf::setp

Función protegida que almacena *_Pbeg* en el puntero inicial y *_Pend* en el puntero final del búfer de salida.

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>Parámetros

*_Pbeg* un puntero al principio del búfer.

*_Pend* un puntero al final del búfer.

## <a name="sgetc"></a>  basic_streambuf::sgetc

Devuelve el elemento actual sin cambiar la posición en la secuencia.

```cpp
int_type sgetc();
```

### <a name="return-value"></a>Valor devuelto

Elemento actual.

### <a name="remarks"></a>Comentarios

Si hay una posición de lectura disponible, la función miembro devuelve **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`*`[gptr](#gptr)). De lo contrario, devuelve [underflow](#underflow).

### <a name="example"></a>Ejemplo

```cpp
// basic_streambuf_sgetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_sgetc.txt", ios::in );

   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
   i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sgetn"></a>  basic_streambuf::sgetn

Extrae hasta *recuento* caracteres del búfer de entrada y los almacena en el búfer proporcionado *ptr*.

Este método es potencialmente inseguro, ya que se basa en el llamador para comprobar que los valores pasados son correctos.

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parámetros

*PTR* el búfer para contener los caracteres extraídos.

*recuento de* el número de elementos que se va a leer.

### <a name="return-value"></a>Valor devuelto

Número de elementos leídos. Vea [streamsize](../standard-library/ios-typedefs.md#streamsize) para obtener más información.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [xsgetn](#xsgetn)(`ptr`, `count`).

### <a name="example"></a>Ejemplo

```cpp
// basic_streambuf_sgetn.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    ifstream myfile("basic_streambuf_sgetn.txt", ios::in);
    char a[10];

    // Extract 3 characters from myfile and store them in a.
    streamsize i = myfile.rdbuf()->sgetn(&a[0], 3);  // C4996
    a[i] = myfile.widen('\0');

    // Display the size and contents of the buffer passed to sgetn.
    cout << i << " " << a << endl;

    // Display the contents of the original input buffer.
    cout << myfile.rdbuf() << endl;
}
```

## <a name="showmanyc"></a>  basic_streambuf::showmanyc

Función miembro virtual protegida que devuelve un recuento del número de caracteres que se pueden extraer del flujo de entrada y garantiza que el programa no esté sujeto a una espera indefinida.

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>Valor devuelto

El comportamiento predeterminado es devolver cero.

## <a name="snextc"></a>  basic_streambuf::snextc

Lee el elemento actual y devuelve el siguiente elemento.

```cpp
int_type snextc();
```

### <a name="return-value"></a>Valor devuelto

Siguiente elemento del flujo.

### <a name="remarks"></a>Comentarios

La función miembro llama a [sbumpc](#sbumpc) y, si esa función devuelve **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), devuelve **traits_type::eof**. De lo contrario, devuelve [sgetc](#sgetc).

### <a name="example"></a>Ejemplo

```cpp
// basic_streambuf_snextc.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->snextc( );
   // cout << ( int )char_traits<char>::eof << endl;
   cout << i << endl;
}
```

```Output

aa

```

```Output

aa97
```

## <a name="sputbackc"></a>  basic_streambuf::sputbackc

Coloca char_type en el flujo.

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>Parámetros

*_Ch* el carácter.

### <a name="return-value"></a>Valor devuelto

Devuelve el carácter o el error.

### <a name="remarks"></a>Comentarios

Si está disponible una posición de devolución y *_Ch* igual que el carácter almacenado en esa posición, la función miembro disminuye el puntero siguiente para el búfer de entrada y devuelve **traits_type::** [ to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`). De lo contrario, devuelve [pbackfail](#pbackfail)(`_Ch`).

### <a name="example"></a>Ejemplo

```cpp
// basic_streambuf_sputbackc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;

    ifstream myfile("basic_streambuf_sputbackc.txt",
        ios::in);

    int i = myfile.rdbuf()->sbumpc();
    cout << (char)i << endl;
    int j = myfile.rdbuf()->sputbackc('z');
    if (j == 'z')
    {
        cout << "it worked" << endl;
    }
    i = myfile.rdbuf()->sgetc();
    cout << (char)i << endl;
}
```

## <a name="sputc"></a>  basic_streambuf::sputc

Coloca un carácter en la secuencia.

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>Parámetros

*_Ch* el carácter.

### <a name="return-value"></a>Valor devuelto

Devuelve el carácter, si se ejecuta correctamente.

### <a name="remarks"></a>Comentarios

Si un `write position` está disponible, la función miembro almacena *_Ch* en la posición de escritura, incrementa el puntero siguiente para el búfer de salida y devuelve **traits_type::**[to_int_type ](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`). De lo contrario, devuelve [overflow](#overflow)(`_Ch`).

### <a name="example"></a>Ejemplo

```cpp
// basic_streambuf_sputc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   int i = cout.rdbuf( )->sputc( 'a' );
   cout << endl << ( char )i << endl;
}
```

```Output
a
a
```

## <a name="sputn"></a>  basic_streambuf::sputn

Coloca una cadena de caracteres en la secuencia.

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parámetros

*PTR* la cadena de caracteres.

*recuento* el recuento de caracteres.

### <a name="return-value"></a>Valor devuelto

Número de caracteres realmente insertados en el flujo.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [xsputn](#xsputn)(`ptr`, `count`). Para más información, vea la sección Comentarios de esta función miembro.

### <a name="example"></a>Ejemplo

```cpp
// basic_streambuf_sputn.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    streamsize i = cout.rdbuf()->sputn("test", 4);
    cout << endl << i << endl;
}
```

```Output
test
4
```

## <a name="stossc"></a>  basic_streambuf::stossc

Mueve más allá del elemento actual de la secuencia.

```cpp
void stossc();
```

### <a name="remarks"></a>Comentarios

La función miembro llama a [sbumpc](#sbumpc). Tenga en cuenta que no se necesita una implementación para proporcionar esta función miembro.

### <a name="example"></a>Ejemplo

```cpp
// basic_streambuf_stossc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_stossc.txt", ios::in );

   myfile.rdbuf( )->stossc( );
   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sungetc"></a>  basic_streambuf::sungetc

Obtiene un carácter de la secuencia.

```cpp
int_type sungetc();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el carácter o un error.

### <a name="remarks"></a>Comentarios

Si hay una posición de devolución disponible, la función miembro disminuye el puntero siguiente para el búfer de entrada y devuelve `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`*`[gptr](#gptr)). Pero no siempre es posible determinar el último carácter leído, por lo que se puede capturar en el estado del búfer actual. Si esto ocurre, la función devuelve [pbackfail](#pbackfail). Para evitar esta situación, realice un seguimiento del carácter que se va a devolver y llame a `sputbackc(ch)`, lo que no producirá un error siempre que no lo llame al principio del flujo ni intente devolver más de un carácter.

### <a name="example"></a>Ejemplo

```cpp
// basic_streambuf_sungetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ifstream myfile( "basic_streambuf_sungetc.txt", ios::in );

   // Read and increment
   int i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Read and increment
   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Decrement, read, and do not increment
   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;
}
```

## <a name="swap"></a>  basic_streambuf::swap

Intercambia los valores de este objeto por los valores del objeto `basic_streambuf` proporcionado.

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*right*|Referencia a un valor L al objeto `basic_streambuf` que se usa para intercambiar valores.|

### <a name="remarks"></a>Comentarios

La función miembro protegida intercambia con *derecho* todos los punteros que controlan la `input buffer` y `output buffer`. También intercambia `right.`[getloc()](#getloc) con el objeto `locale`.

## <a name="sync"></a>  basic_streambuf::sync

Función virtual protegida que intenta sincronizar las secuencias controladas con cualquier secuencia externa asociada.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Valor devuelto

Si la función no se puede ejecutar correctamente, devuelve -1. El comportamiento predeterminado es devolver cero.

### <a name="remarks"></a>Comentarios

`sync` implica escribir cualquier elemento entre los punteros inicial y siguientes para el búfer de salida. No conlleva devolver ningún elemento entre los punteros siguientes y final para el búfer de entrada.

## <a name="traits_type"></a>  basic_streambuf::traits_type

Asocia un nombre de tipo al parámetro de plantilla **Tr**.

```cpp
typedef Tr traits_type;
```

## <a name="uflow"></a>  basic_streambuf::uflow

Función virtual protegida que extrae el elemento actual del flujo de entrada.

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>Valor devuelto

Elemento actual.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida intenta extraer el elemento actual **ch** del flujo de entrada, avanzar la posición de flujo actual y devolver el elemento como **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)(**ch**). Puede hacerlo de varias maneras:

- Si hay una posición de lectura disponible, toma **ch** como elemento almacenado en la posición de lectura y avanza el puntero siguiente del búfer de entrada.

- Puede leer un elemento directamente, desde algún origen externo, y ofrecerlo como valor **ch**.

- En el caso de un búfer de flujo con flujos de entrada y salida comunes, puede facilitar una posición de lectura al escribir en algún destino externo algunos o todos los elementos situados entre los punteros inicial y siguientes para el búfer de salida. O bien puede asignar almacenamiento nuevo o adicional para el búfer de entrada. Luego la función lee, desde algún origen externo, uno o más elementos.

Si la función no se ejecuta correctamente, devuelve **traits_type::**[eof](../standard-library/char-traits-struct.md#eof) o inicia una excepción. De lo contrario, devuelve el elemento actual `ch` en el flujo de entrada, convertido tal como se ha descrito arriba, y avanza el puntero siguiente para el búfer de entrada. El comportamiento predeterminado es llamar a [underflow](#underflow) y, si esa función devuelve **traits_type::eof**, devolver **traits_type::eof**. De lo contrario, la función devuelve el elemento actual **ch** en el flujo de entrada, convertido tal como se ha descrito anteriormente, y avanza el puntero siguiente para el búfer de entrada.

## <a name="underflow"></a>  basic_streambuf::underflow

Función virtual protegida que extrae el elemento actual de la secuencia de entrada.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Valor devuelto

Elemento actual.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida intenta extraer el elemento actual **ch** del flujo de entrada, sin avanzar la posición de flujo actual, y devolverlo como `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)(**ch**). Puede hacerlo de varias maneras:

- Si hay una posición de lectura disponible, **ch** es el elemento almacenado en la posición de lectura. Para más información sobre esto, vea la sección Comentarios de [basic_streambuf (Clase)](../standard-library/basic-streambuf-class.md).

- Puede facilitar una posición de lectura mediante la asignación de almacenamiento nuevo o adicional para el búfer de entrada y luego leer, desde algún origen externo, uno o más elementos. Para más información sobre esto, vea la sección Comentarios de [basic_streambuf (Clase)](../standard-library/basic-streambuf-class.md).

Si la función no se puede ejecutar correctamente, devuelve `traits_type::`[eof](../standard-library/char-traits-struct.md#eof)`()` o inicia una excepción. De lo contrario, devuelve el elemento actual en el flujo de entrada, convertido tal como se ha descrito anteriormente. El comportamiento predeterminado es devolver `traits_type::eof()`.

La función virtual `underflow`, junto con las funciones [sync](#sync) y [overflow](#overflow), define las características de la clase derivada de `streambuf`. Cada clase derivada podría implementar `underflow` de manera diferente, pero la interfaz con la clase stream que realiza la llamada es igual.

La función `underflow` recibe llamadas con más frecuencia de funciones públicas `streambuf` como [sgetc](#sgetc) y [sgetn](#sgetn) cuando el área de obtención está llena, pero otras clases, incluidas las clases stream, pueden llamar a `underflow` en cualquier momento.

La función `underflow` proporciona al área de obtención caracteres desde el origen de entrada. Si el área de obtención contiene caracteres, `underflow` devuelve el primero. Si el área de obtención está vacía, la llena y devuelve el siguiente carácter (que deja en el área de obtención). Si no hay más caracteres disponibles, `underflow` devuelve `EOF` y deja vacía el área de obtención.

En la clase `strstreambuf`, `underflow` ajusta el puntero [egptr](#egptr) para acceder al almacenamiento asignado dinámicamente mediante una llamada a `overflow`.

## <a name="xsgetn"></a>  basic_streambuf::xsgetn

Función virtual protegida para extraer elementos del flujo de entrada.

Este método es potencialmente inseguro, ya que se basa en el llamador para comprobar que los valores pasados son correctos.

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parámetros

*PTR* el búfer para contener los caracteres extraídos.

*recuento de* el número de elementos que se va a extraer.

### <a name="return-value"></a>Valor devuelto

Número de elementos extraídos.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida extrae hasta *recuento* elementos de la secuencia de entrada como si realizara llamadas repetidas a [sbumpc](#sbumpc)y los almacena en la matriz a partir *ptr*. Devuelve el número de elementos realmente extraídos.

## <a name="xsputn"></a>  basic_streambuf::xsputn

Función virtual protegida para insertar elementos en el flujo de salida.

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parámetros

*PTR* puntero a los elementos se va a insertar.

*recuento* número de elementos que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Número de elementos realmente insertados en el flujo.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida inserta hasta *recuento* elementos en la salida de stream, como si realizara llamadas repetidas a [sputc](#sputc), desde el principio de la matriz en *ptr*. La inserción de caracteres en el flujo de salida una vez detiene todos *recuento* se han escrito caracteres, o si una llamada a `sputc( count)` devolvería `traits::eof()`. Devuelve el número de elementos realmente insertados.

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
