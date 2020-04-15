---
title: time_put (Clase)
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
ms.openlocfilehash: 10691de0a583dc7d5a66c319968d90978bf59480
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367998"
---
# <a name="time_put-class"></a>time_put (Clase)

La plantilla de clase describe un objeto que puede servir como una faceta `CharType`de configuración regional para controlar las conversiones de valores de tiempo a secuencias de tipo .

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Parámetros

*CharType*\
Tipo usado dentro de un programa para codificar caracteres.

*OutputIterator*\
El tipo de iterador en el que las funciones time put escriben sus resultados.

## <a name="remarks"></a>Observaciones

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[time_put](#time_put)|Constructor para los objetos de tipo `time_put`.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|
|[iter_type](#iter_type)|Tipo que describe un iterador de salida.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[do_put](#do_put)|Una función virtual que genera información de hora y fecha como una secuencia de `CharType`s.|
|[put](#put)|Genera información de hora y fecha como una secuencia de `CharType`s.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="time_putchar_type"></a><a name="char_type"></a>time_put::char_type

Tipo que se usa para describir un carácter empleado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `CharType`.

## <a name="time_putdo_put"></a><a name="do_put"></a>time_put::do_put

Una función virtual que genera información de hora y fecha como una secuencia de `CharType`s.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parámetros

*próximo*\
Un iterador de salida en el que se va a insertar la secuencia de caracteres que representan la fecha y la hora.

*_Iosbase*\
Sin usar.

*_Pt*\
La información de fecha y hora que se va a representar.

*_Fmt*\
El formato de la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

*_Mod*\
Un modificador para el formato. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

### <a name="return-value"></a>Valor devuelto

Un iterador a la primera posición después del último elemento insertado.

### <a name="remarks"></a>Observaciones

La función miembro protegido virtual `next` genera elementos secuenciales a partir de los valores de tiempo almacenados en el objeto \* `_Pt`, de tipo `tm`. La función devuelve un iterador que designa el lugar siguiente para insertar un elemento más allá de la salida generada.

La salida se genera mediante las `strftime`mismas reglas utilizadas por , con un último argumento de *_Pt*, para generar una serie de elementos **char** en una matriz. Se supone que cada elemento **char** se `CharType` asigna a un elemento equivalente de tipo mediante una asignación simple de uno a uno. Si *_Mod* es igual a cero, el formato efectivo es "%F", donde F se sustituye por *_Fmt*. De lo contrario, el formato efectivo es "%MF", donde M se sustituye por *_Mod*.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [put](#put), que llama a `do_put`.

## <a name="time_putiter_type"></a><a name="iter_type"></a>time_put::iter_type

Tipo que describe un iterador de salida.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `OutputIterator`.

## <a name="time_putput"></a><a name="put"></a>time_put::put

Genera información de hora y fecha como una secuencia de `CharType`s.

```cpp
iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;

iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*próximo*\
Un iterador de salida en el que se va a insertar la secuencia de caracteres que representan la fecha y la hora.

*_Iosbase*\
Sin usar.

*_Fill*\
Carácter de `CharType` tipo utilizado para el espaciado.

*_Pt*\
La información de fecha y hora que se va a representar.

*_Fmt*\
El formato de la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

*_Mod*\
Un modificador para el formato. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

*Primero*\
El principio de la cadena de formato para la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

*Última*\
El final de la cadena de formato para la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

### <a name="return-value"></a>Valor devuelto

Un iterador a la primera posición después del último elemento insertado.

### <a name="remarks"></a>Observaciones

La primera función`next`miembro `_Iosbase` `_Fill`devuelve `_Pt` `_Fmt`do_put `_Mod`( , , , , , . . [do_put](#do_put) La segunda función \* `next` miembro copia en ++ cualquier elemento del intervalo [ `first`, `last`) que no sea un porcentaje (%). Para un porcentaje seguido *C* de un `first`carácter C en el intervalo [ `last`, ), la función en su lugar evalúa `next`  =  `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) y omite más allá de *C*. Sin embargo, si *C* es un carácter calificador del `C2` conjunto EOQ, seguido de un carácter en el intervalo [ `first` `last`, ), la función en su lugar evalúa `next`  =  `do_put` `next`( , `_Iosbase`, `_Fill`, `_Pt`, , `C2`, *C*) y omite más allá `C2`.

### <a name="example"></a>Ejemplo

```cpp
// time_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   t.tm_hour = 5;
   t.tm_min = 30;
   t.tm_sec = 40;
   t.tm_year = 00;
   t.tm_mday = 4;
   t.tm_mon = 6;

   pszPutI.imbue( loc );
   char *pattern = "x: %X %x";
   use_facet <time_put <char> >
   (loc).put(basic_ostream<char>::_Iter(pszPutI.rdbuf( )),
          pszPutI, ' ', &t, pattern, pattern+strlen(pattern));

      cout << "num_put( ) = " << pszPutI.rdbuf( )->str( ) << endl;

      char strftimebuf[255];
      strftime(&strftimebuf[0], 255, pattern, &t);
      cout << "strftime( ) = " << &strftimebuf[0] << endl;
}
```

```Output
num_put( ) = x: 05:30:40 07/04/00
strftime( ) = x: 05:30:40 07/04/00
```

## <a name="time_puttime_put"></a><a name="time_put"></a>time_put::time_put

Constructor para los objetos de tipo `time_put`.

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

*_Refs*\
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

### <a name="remarks"></a>Observaciones

Los valores posibles para el parámetro *_Refs* y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \>1: Estos valores no están definidos.

El constructor inicializa su objeto base con [locale::facet](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="see-also"></a>Consulte también

[\<>de la localidad](../standard-library/locale.md)\
[Clase time_base](../standard-library/time-base-class.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
