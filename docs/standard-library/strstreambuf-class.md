---
title: strstreambuf (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2424ce23c0a376156bbb78869a2e33e501958e73
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719139"
---
# <a name="strstreambuf-class"></a>strstreambuf (Clase)

Describe un búfer de secuencia que controla la transmisión de elementos a y desde una secuencia de elementos almacenados en un **char** objeto array.

## <a name="syntax"></a>Sintaxis

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Comentarios

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

|Función miembro|Descripción|
|-|-|
|[freeze](#freeze)|Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.|
|[overflow](#overflow)|Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.|
|[pbackfail](#pbackfail)|Función miembro virtual protegida que intenta recolocar un elemento en el flujo de entrada y, después, convertirlo en el elemento actual (al que apunta el puntero siguiente).|
|[pcount](#pcount)|Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.|
|[seekoff](#seekoff)|Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.|
|[seekpos](#seekpos)|Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.|
|[str](#str)|Llama a [freeze](#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.|
|[underflow](#underflow)|Función virtual protegida que extrae el elemento actual del flujo de entrada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<strstream>

**Espacio de nombres:** std

## <a name="freeze"></a>  strstreambuf::freeze

Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parámetros

*_Freezeit*<br/>
Un **bool** que indica si desea que la secuencia se detenga.

### <a name="remarks"></a>Comentarios

Si *_Freezeit* es true, la función modifica almacenado `strstreambuf` modo para que la secuencia controlada inmovilizada. De lo contrario, hace que la secuencia controlada no esté inmovilizada.

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

## <a name="overflow"></a>  strstreambuf::overflow

Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>Parámetros

*_Meta*<br/>
El carácter que se va a insertar en el búfer o `EOF`.

### <a name="return-value"></a>Valor devuelto

Si la función no se ejecuta correctamente, devuelve `EOF`. De lo contrario, si _ *Meta* == `EOF`, devuelve un valor distinto de `EOF`. De lo contrario, devuelve \_ *Meta*.

### <a name="remarks"></a>Comentarios

Si _ *Meta* != `EOF`, la función miembro virtual protegida intenta insertar el elemento ( `char`)\_ *Meta* en el búfer de salida. Puede hacerlo de varias maneras:

- Si está disponible una posición de escritura, puede almacenar el elemento en la posición de escritura e incrementar el puntero siguiente para el búfer de salida.

- Si el modo de strstreambuf almacenado indica que la secuencia controlada es modificable, ampliable y no está inmovilizada, la función puede disponer de una posición de escritura mediante la asignación de new para el búfer de salida. Extender el búfer de salida de esta forma también extiende cualquier búfer de entrada asociado.

## <a name="pbackfail"></a>  strstreambuf::pbackfail

Una función miembro virtual protegida que intenta devolver un elemento al flujo de entrada y, después, convertirlo en el elemento actual (al que apunta el puntero siguiente).

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>Parámetros

*_Meta*<br/>
El carácter que se va a insertar en el búfer o `EOF`.

### <a name="return-value"></a>Valor devuelto

Si la función no se ejecuta correctamente, devuelve `EOF`. De lo contrario, si _ *Meta* == `EOF`, devuelve un valor distinto de `EOF`. De lo contrario, devuelve \_ *Meta*.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida intenta devolver un elemento al búfer de entrada y, después, convertirlo en el elemento actual (indicado por el siguiente puntero).

Si _ *Meta* == `EOF`, el elemento que se va a devolver es realmente el que ya está en el flujo por delante del elemento actual. De lo contrario, dicho elemento se sustituye por **ch** = ( `char`)\_ *Meta*. La función puede devolver un elemento de distintas maneras:

- Si está disponible una posición de devolución y el elemento almacenado es igual a `ch`, puede disminuir el puntero siguiente del búfer de entrada.

- Si está disponible una posición de devolución y si el modo de strstreambuf indica que la secuencia controlada es modificable, la función puede almacenar `ch` en la posición de devolución y disminuir el puntero siguiente del búfer de entrada.

## <a name="pcount"></a>  strstreambuf::pcount

Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valor devuelto

Un recuento del número de elementos que se escriben en la secuencia controlada.

### <a name="remarks"></a>Comentarios

En concreto, si [pptr](../standard-library/basic-streambuf-class.md#pptr) es un puntero nulo, la función devuelve cero. De lo contrario, devuelve `pptr`  -  [pbase](../standard-library/basic-streambuf-class.md#pbase).

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

## <a name="seekoff"></a>  strstreambuf::seekoff

Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Off*<br/>
La posición para buscar relativa a *_Way*.

*_Way*<br/>
El punto de partida de las operaciones de desplazamiento. Vea los valores posibles en [seekdir](../standard-library/ios-base-class.md#seekdir).

*_Which*<br/>
Especifica el modo de la posición del puntero. El valor predeterminado es permitirle modificar las posiciones de lectura y escritura.

### <a name="return-value"></a>Valor devuelto

Si la función modifica correctamente una o las dos posiciones de la secuencia, devuelve la posición de la secuencia resultante. De lo contrario, se produce un error y devuelve una posición de secuencia no válida.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas. Para un objeto de la clase strstreambuf, una posición de la secuencia consta únicamente de un desplazamiento de la secuencia. El desplazamiento cero designa el primer elemento de la secuencia controlada.

La nueva posición se determina de la siguiente forma:

- Si `_Way` == `ios_base::beg`, la nueva posición es el principio del flujo más _ *Off*.

- Si `_Way` == `ios_base::cur`, la nueva posición es la posición actual del flujo más _ *Off*.

- Si `_Way` == `ios_base::end`, la nueva posición es el final de la secuencia más _ *Off*.

Si `_Which` & **ios_base::in** es distinto de cero y el búfer de entrada existe, la función modifica la siguiente posición de lectura en el búfer de entrada. Si `_Which` & **ios_base::out** también es distinto de cero, `_Way` != **ios_base::cur** y existe el búfer de salida, la función establece también la siguiente posición de escritura para que coincida con la siguiente posición de lectura.

De lo contrario, si `_Which` & `ios_base::out` es distinto de cero y el búfer de salida existe, la función modifica la siguiente posición de escritura en el búfer de salida. De lo contrario, se produce un error en la operación de posicionamiento. Para que una operación de posicionamiento se realice correctamente, la posición de la secuencia resultante debe encontrarse dentro de la secuencia controlada.

## <a name="seekpos"></a>  strstreambuf::seekpos

Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Sp*<br/>
La posición que se va a buscar.

*_Which*<br/>
Especifica el modo de la posición del puntero. El valor predeterminado es permitirle modificar las posiciones de lectura y escritura.

### <a name="return-value"></a>Valor devuelto

Si la función modifica correctamente una o las dos posiciones de la secuencia, devuelve la posición de la secuencia resultante. De lo contrario, se produce un error y devuelve una posición de flujo no válida. Para determinar si la posición del flujo no es válida, compare el valor devuelto con `pos_type(off_type(-1))`.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida trata de modificar las posiciones actuales de las secuencias controladas. Para un objeto de la clase strstreambuf, una posición de la secuencia consta únicamente de un desplazamiento de la secuencia. El desplazamiento cero designa el primer elemento de la secuencia controlada. La nueva posición se determina mediante _ *Sp*.

Si `_Which` & **ios_base::in** es distinto de cero y el búfer de entrada existe, la función modifica la siguiente posición de lectura en el búfer de entrada. Si `_Which` & `ios_base::out` es distinto de cero y existe el búfer de salida, la función establece también la siguiente posición de escritura para que coincida con la siguiente posición de lectura. De lo contrario, si `_Which` & `ios_base::out` es distinto de cero y el búfer de salida existe, la función modifica la siguiente posición de escritura en el búfer de salida. De lo contrario, se produce un error en la operación de posicionamiento. Para que una operación de posicionamiento se realice correctamente, la posición del flujo resultante debe encontrarse dentro de la secuencia controlada.

## <a name="str"></a>  strstreambuf::str

Llama a [freeze](#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.

```cpp
char *str();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al principio de la secuencia controlada.

### <a name="remarks"></a>Comentarios

No existe ningún elemento nulo de terminación, a menos que inserte explícitamente uno.

### <a name="example"></a>Ejemplo

Vea [strstreambuf::freeze](#freeze) para obtener un ejemplo que usa **str**.

## <a name="strstreambuf"></a>  strstreambuf::strstreambuf

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

*_Allocfunc*<br/>
La función que se usa para asignar memoria de búfer.

*count*<br/>
Determina la longitud del búfer señalado por *_Getptr*. Si *_Getptr* no es un argumento (primer formulario constructor), el tamaño de una asignación sugerida para los búferes.

*_Freefunc*<br/>
La función que se usa para liberar memoria de búfer.

*_Getptr*<br/>
Un búfer que se usa para la entrada.

*_Putptr*<br/>
Un búfer que se usa para la salida.

### <a name="remarks"></a>Comentarios

El primer constructor almacena un puntero nulo en todos los punteros que controlan el búfer de entrada, el búfer de salida y la asignación de strstreambuf. Establece el modo de strstreambuf almacenado para que la secuencia controlada se pueda modificar y ampliar. También acepta *recuento* como un tamaño de asignación inicial sugerido.

El segundo constructor se comporta como el primero, salvo que almacena _ *Allocfunc* como puntero a la función que se llama para asignar el almacenamiento y \_ *Freefunc* como puntero a la función que se llama para liberar el almacenamiento.

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

También se comportan como el primero, salvo que `_Getptr` designa el objeto de matriz que se usa para contener la secuencia controlada. (Por tanto, no debe ser un puntero nulo). El número de elementos *N* en la matriz se determina como sigue:

- Si (`count` > 0), a continuación, *N* es `count`.

- Si (`count` == 0), a continuación, *N* es `strlen`(( **const** `char` *) `_Getptr` ).

- Si (`count` < 0), a continuación, *N* es **INT_MAX**.

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

## <a name="underflow"></a>  strstreambuf::underflow

Función virtual protegida que extrae el elemento actual del flujo de entrada.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>Valor devuelto

Si la función no se ejecuta correctamente, devuelve `EOF`. De lo contrario, devuelve el elemento actual en el flujo de entrada, convertido tal y como se describió anteriormente.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida intenta extraer el elemento actual `ch` del búfer de entrada y, a continuación, avanzar la posición actual del flujo y devolver el elemento como (`int`) (`unsigned char`) **ch**. Puede hacerlo en solo una manera: si una posición de lectura está disponible, toma `ch` como el elemento almacenado en la posición de lectura y avanza el puntero siguiente del búfer de entrada.

## <a name="see-also"></a>Vea también

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
