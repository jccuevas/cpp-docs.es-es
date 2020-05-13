---
title: strstreambuf (Clase)
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
helpviewer_keywords:
- std::strstreambuf [C++], freeze
- std::strstreambuf [C++], overflow
- std::strstreambuf [C++], pbackfail
- std::strstreambuf [C++], pcount
- std::strstreambuf [C++], seekoff
- std::strstreambuf [C++], seekpos
- std::strstreambuf [C++], str
- std::strstreambuf [C++], underflow
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
ms.openlocfilehash: 28399a1cd55407aadbc5d59e1e835892218ad0c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376610"
---
# <a name="strstreambuf-class"></a>strstreambuf (Clase)

Describe un búfer de secuencia que controla la transmisión de elementos hacia y desde una secuencia de elementos almacenados en un objeto de matriz **char.**

## <a name="syntax"></a>Sintaxis

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Observaciones

En función de cómo se haya construido el objeto, se puede asignar, extender y liberar según sea necesario para dar cabida a los cambios en la secuencia.

Un objeto de clase `strstreambuf` almacena varios bits de información de modo como su modo `strstreambuf`. Estos bits indican si la secuencia controlada:

- Se ha asignado y debe liberarse finalmente.

- Es modificable.

- Es extensible mediante la reasignación de almacenamiento.

- Se ha quedado inmovilizada y, por tanto, se debe movilizar antes de que se destruya el objeto o liberar (en el caso de estar asignado) por parte de un organismo que no sea el objeto.

Una secuencia controlada inmovilizada no se puede modificar ni extender, independientemente del estado de estos bits de modo independiente.

El objeto también almacena punteros a dos funciones que controlan la asignación `strstreambuf`. Si se trata de punteros nulos, el objeto diseña su propio método para asignar y liberar el almacenamiento de la secuencia controlada.

> [!NOTE]
> Esta clase está en desuso. Considere el uso de [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) o [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf) en su lugar.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[strstreambuf](#strstreambuf)|Construye un objeto de tipo `strstreambuf`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Congelar](#freeze)|Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.|
|[Desbordamiento](#overflow)|Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.|
|[pbackfail](#pbackfail)|Función miembro virtual protegida que intenta recolocar un elemento en el flujo de entrada y, después, convertirlo en el elemento actual (al que apunta el puntero siguiente).|
|[pcount](#pcount)|Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.|
|[seekoff](#seekoff)|Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.|
|[seekpos](#seekpos)|Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.|
|[Str](#str)|Llama a [freeze](#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.|
|[Desbordamiento](#underflow)|Función virtual protegida que extrae el elemento actual del flujo de entrada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<strstream>

**Espacio de nombres:** std

## <a name="strstreambuffreeze"></a><a name="freeze"></a>strstreambuf::freeze

Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parámetros

*_Freezeit*\
Un **bool** que indica si desea que la secuencia se congele.

### <a name="remarks"></a>Observaciones

Si *_Freezeit* es true, la `strstreambuf` función modifica el modo almacenado para que la secuencia controlada se incongele. De lo contrario, hace que la secuencia controlada no esté inmovilizada.

[str](#str) implica `freeze`.

> [!NOTE]
> Un búfer inmovilizado no se liberará durante la destrucción de `strstreambuf`. Debe liberar el búfer antes de que se libere para evitar una pérdida de memoria.

### <a name="example"></a>Ejemplo

```cpp
// strstreambuf_freeze.cpp
// compile with: /EHsc

#include <iostream>
#include <strstream>

using namespace std;

void report(strstream &x)
{
    if (!x.good())
        cout << "stream bad" << endl;
    else
        cout << "stream good" << endl;
}

int main()
{
    strstream x;

    x << "test1";
    cout << "before freeze: ";
    report(x);

    // Calling str freezes stream.
    cout.write(x.rdbuf()->str(), 5) << endl;
    cout << "after freeze: ";
    report(x);

    // Stream is bad now, wrote on frozen stream
    x << "test1.5";
    cout << "after write to frozen stream: ";
    report(x);

    // Unfreeze stream, but it is still bad
    x.rdbuf()->freeze(false);
    cout << "after unfreezing stream: ";
    report(x);

    // Clear stream
    x.clear();
    cout << "after clearing stream: ";
    report(x);

    x << "test3";
    cout.write(x.rdbuf()->str(), 10) << endl;

    // Clean up.  Failure to unfreeze stream will cause a
    // memory leak.
    x.rdbuf()->freeze(false);
}
```

```Output
before freeze: stream good
test1
after freeze: stream good
after write to frozen stream: stream bad
after unfreezing stream: stream bad
after clearing stream: stream good
test1test3
```

## <a name="strstreambufoverflow"></a><a name="overflow"></a>strstreambuf::overflow

Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>Parámetros

*_Meta*\
El carácter que se va a insertar en el búfer o `EOF`.

### <a name="return-value"></a>Valor devuelto

Si la función no se ejecuta correctamente, devuelve `EOF`. De lo * \_* contrario, si Meta == `EOF` `EOF`, devuelve algún valor distinto de . De lo * \_* contrario, devuelve Meta .

### <a name="remarks"></a>Observaciones

Si * \_Meta* `EOF`! , la función miembro `(char)_Meta` virtual protegida intenta insertar el elemento en el búfer de salida. Puede hacerlo de varias maneras:

- Si está disponible una posición de escritura, puede almacenar el elemento en la posición de escritura e incrementar el puntero siguiente para el búfer de salida.

- Si el modo de strstreambuf almacenado indica que la secuencia controlada es modificable, ampliable y no está inmovilizada, la función puede disponer de una posición de escritura mediante la asignación de new para el búfer de salida. Extender el búfer de salida de esta forma también extiende cualquier búfer de entrada asociado.

## <a name="strstreambufpbackfail"></a><a name="pbackfail"></a>strstreambuf::pbackfail

Una función miembro virtual protegida que intenta devolver un elemento al flujo de entrada y, después, convertirlo en el elemento actual (al que apunta el puntero siguiente).

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>Parámetros

*_Meta*\
El carácter que se va a insertar en el búfer o `EOF`.

### <a name="return-value"></a>Valor devuelto

Si la función no se ejecuta correctamente, devuelve `EOF`. De lo * \_* contrario, si Meta == `EOF` `EOF`, devuelve algún valor distinto de . De lo * \_* contrario, devuelve Meta .

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida intenta devolver un elemento al búfer de entrada y, después, convertirlo en el elemento actual (indicado por el siguiente puntero).

Si * \_Meta* == `EOF`, el elemento que se va a empujar hacia atrás es efectivamente el que ya está en la secuencia antes que el elemento actual. De lo contrario, ese `ch = (char)_Meta`elemento se sustituye por . La función puede devolver un elemento de distintas maneras:

- Si una posición de devolución está disponible y el `ch`elemento almacenado allí se compara igual a , puede disminuir el puntero siguiente para el búfer de entrada.

- Si una posición de devolución está disponible, y si el modo strstreambuf dice `ch` que la secuencia controlada es modificable, la función puede almacenar en la posición de devolución y disminuir el puntero siguiente para el búfer de entrada.

## <a name="strstreambufpcount"></a><a name="pcount"></a>strstreambuf::pcount

Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valor devuelto

Un recuento del número de elementos que se escriben en la secuencia controlada.

### <a name="remarks"></a>Observaciones

En concreto, si [pptr](../standard-library/basic-streambuf-class.md#pptr) es un puntero nulo, la función devuelve cero. De lo `pptr`  - contrario, devuelve [pbase](../standard-library/basic-streambuf-class.md#pbase).

### <a name="example"></a>Ejemplo

```cpp
// strstreambuf_pcount.cpp
// compile with: /EHsc
#include <iostream>
#include <strstream>
using namespace std;

int main( )
{
   strstream x;
   x << "test1";
   cout << x.rdbuf( )->pcount( ) << endl;
   x << "test2";
   cout << x.rdbuf( )->pcount( ) << endl;
}
```

## <a name="strstreambufseekoff"></a><a name="seekoff"></a>strstreambuf::seekoff

Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.

```cpp
virtual streampos seekoff(streamoff _Off,
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

Si la función modifica correctamente una o las dos posiciones de la secuencia, devuelve la posición de la secuencia resultante. De lo contrario, se produce un error y devuelve una posición de secuencia no válida.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas. Para un objeto de la clase strstreambuf, una posición de la secuencia consta únicamente de un desplazamiento de la secuencia. El desplazamiento cero designa el primer elemento de la secuencia controlada.

La nueva posición se determina de la siguiente forma:

- Si `_Way == ios_base::beg`, la nueva posición es el principio de la secuencia más *_Off*.

- Si `_Way == ios_base::cur`, la nueva posición es la posición actual de la secuencia más *_Off*.

- Si `_Way == ios_base::end`, la nueva posición es el final de la secuencia más *_Off*.

Si `_Which & ios_base::in` es distinto de cero y existe el búfer de entrada, la función modifica la siguiente posición para leer en el búfer de entrada. Si `_Which & ios_base::out` también es `_Way != ios_base::cur`distinto de cero, , y existe el búfer de salida, la función también establece la siguiente posición para escribir para que coincida con la siguiente posición para leer.

De lo contrario, si `_Which & ios_base::out` es distinto de cero y el búfer de salida existe, la función modifica la siguiente posición de escritura en el búfer de salida. De lo contrario, se produce un error en la operación de posicionamiento. Para que una operación de posicionamiento se realice correctamente, la posición del flujo resultante debe encontrarse dentro de la secuencia controlada.

## <a name="strstreambufseekpos"></a><a name="seekpos"></a>strstreambuf::seekpos

Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Sp*\
La posición que se va a buscar.

*_Which*\
Especifica el modo de la posición del puntero. El valor predeterminado es permitirle modificar las posiciones de lectura y escritura.

### <a name="return-value"></a>Valor devuelto

Si la función modifica correctamente una o las dos posiciones de la secuencia, devuelve la posición de la secuencia resultante. De lo contrario, se produce un error y devuelve una posición de secuencia no válida. Para determinar si la posición del flujo no es válida, compare el valor devuelto con `pos_type(off_type(-1))`.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas. Para un objeto de la clase strstreambuf, una posición de la secuencia consta únicamente de un desplazamiento de la secuencia. El desplazamiento cero designa el primer elemento de la secuencia controlada. La nueva posición viene determinada por *_Sp*.

Si `_Which` & **ios_base::in** es distinto de cero y el búfer de entrada existe, la función modifica la siguiente posición de lectura en el búfer de entrada. Si `_Which` & `ios_base::out` es distinto de cero y existe el búfer de salida, la función establece también la siguiente posición de escritura para que coincida con la siguiente posición de lectura. De lo contrario, si `_Which` & `ios_base::out` es distinto de cero y el búfer de salida existe, la función modifica la siguiente posición de escritura en el búfer de salida. De lo contrario, se produce un error en la operación de posicionamiento. Para que una operación de posicionamiento se realice correctamente, la posición del flujo resultante debe encontrarse dentro de la secuencia controlada.

## <a name="strstreambufstr"></a><a name="str"></a>strstreambuf::str

Llama a [freeze](#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.

```cpp
char *str();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al principio de la secuencia controlada.

### <a name="remarks"></a>Observaciones

No existe ningún elemento nulo de terminación, a menos que inserte explícitamente uno.

### <a name="example"></a>Ejemplo

Vea [strstreambuf::freeze](#freeze) para obtener un ejemplo que usa **str**.

## <a name="strstreambufstrstreambuf"></a><a name="strstreambuf"></a>strstreambuf::strstreambuf

Construye un objeto de tipo `strstreambuf`.

```cpp
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* _Allocfunc)(size_t),
    void (* _Freefunc)(void*));

strstreambuf(char* _Getptr,
    streamsize count,
    char* _Putptr = 0);

strstreambuf(signed char* _Getptr,
    streamsize count,
    signed char* _Putptr = 0);

strstreambuf(unsigned char* _Getptr,
    streamsize count,
    unsigned char* _Putptr = 0);

strstreambuf(const char* _Getptr,
    streamsize count);

strstreambuf(const signed char* _Getptr,
    streamsize count);

strstreambuf(const unsigned char* _Getptr,
    streamsize count);
```

### <a name="parameters"></a>Parámetros

*_Allocfunc*\
La función que se usa para asignar memoria de búfer.

*Contar*\
Determina la longitud del búfer al que apunta *_Getptr*. Si *_Getptr* no es un argumento (primer formulario de constructor), un tamaño de asignación sugerido para los búferes.

*_Freefunc*\
La función que se usa para liberar memoria de búfer.

*_Getptr*\
Un búfer que se usa para la entrada.

*_Putptr*\
Un búfer que se usa para la salida.

### <a name="remarks"></a>Observaciones

El primer constructor almacena un puntero nulo en todos los punteros que controlan el búfer de entrada, el búfer de salida y la asignación de strstreambuf. Establece el modo de strstreambuf almacenado para que la secuencia controlada se pueda modificar y ampliar. También acepta *count* como un tamaño de asignación inicial sugerido.

El segundo constructor se comporta como el primero, excepto que almacena * \_Allocfunc* como el puntero a la función para llamar para asignar almacenamiento y * \_Freefunc* como el puntero a la función para llamar para liberar ese almacenamiento.

Los tres constructores:

```cpp
strstreambuf(char *_Getptr,
    streamsize count,
    char *putptr = 0);

strstreambuf(signed char *_Getptr,
    streamsize count,
    signed char *putptr = 0);

strstreambuf(unsigned char *_Getptr,
    streamsize count,
    unsigned char *putptr = 0);
```

También se comportan como el primero, salvo que `_Getptr` designa el objeto de matriz que se usa para contener la secuencia controlada. (Por lo tanto, no debe ser un puntero nulo.) El número de elementos *N* de la matriz se determina de la siguiente manera:

- Si`count` ( > 0), `count`entonces *N* es .

- Si`count` ( ) 0), `strlen`entonces *N* es `_Getptr` ( ( **const** `char` *) ).

- Si`count` ( < 0), *n* se **INT_MAX**.

Si `_Putptr` es un puntero nulo, la función solo establece un búfer de entrada mediante la ejecución de:

```cpp
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```

De lo contrario, establece los búferes de entrada y salida mediante la ejecución de:

```cpp
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```

En este caso, `_Putptr` debe estar en el intervalo [ `_Getptr`, `_Getptr` + *N*].

Por último, los tres constructores:

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

se comportan igual que:

```cpp
streambuf((char *)_Getptr, count);
```

salvo que el modo almacenado hace que la secuencia controlada no se pueda modificar ni ampliar.

## <a name="strstreambufunderflow"></a><a name="underflow"></a>strstreambuf::underflow

Función virtual protegida que extrae el elemento actual del flujo de entrada.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>Valor devuelto

Si la función no se ejecuta correctamente, devuelve `EOF`. De lo contrario, devuelve el elemento actual en el flujo de entrada, convertido tal y como se describió anteriormente.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida se `ch` esfuerza por extraer el elemento actual del búfer`int`de`unsigned char`entrada, a continuación, avanzar la posición actual de la secuencia y devolver el elemento como ( )( ) **ch**. Puede hacerlo de una sola manera: si una posición `ch` de lectura está disponible, toma como elemento almacenado en la posición de lectura y avanza el puntero siguiente para el búfer de entrada.

## <a name="see-also"></a>Consulte también

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
