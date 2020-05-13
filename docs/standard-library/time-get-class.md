---
title: time_get (Clase)
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get
- locale/std::time_get::char_type
- locale/std::time_get::iter_type
- locale/std::time_get::date_order
- locale/std::time_get::do_date_order
- locale/std::time_get::do_get
- locale/std::time_get::do_get_date
- locale/std::time_get::do_get_monthname
- locale/std::time_get::do_get_time
- locale/std::time_get::do_get_weekday
- locale/std::time_get::do_get_year
- locale/std::time_get::get
- locale/std::time_get::get_date
- locale/std::time_get::get_monthname
- locale/std::time_get::get_time
- locale/std::time_get::get_weekday
- locale/std::time_get::get_year
helpviewer_keywords:
- std::time_get [C++]
- std::time_get [C++], char_type
- std::time_get [C++], iter_type
- std::time_get [C++], date_order
- std::time_get [C++], do_date_order
- std::time_get [C++], do_get
- std::time_get [C++], do_get_date
- std::time_get [C++], do_get_monthname
- std::time_get [C++], do_get_time
- std::time_get [C++], do_get_weekday
- std::time_get [C++], do_get_year
- std::time_get [C++], get
- std::time_get [C++], get_date
- std::time_get [C++], get_monthname
- std::time_get [C++], get_time
- std::time_get [C++], get_weekday
- std::time_get [C++], get_year
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
ms.openlocfilehash: 9aebdaffc8bf3754bdbda08247f72ae08475711f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368040"
---
# <a name="time_get-class"></a>time_get (Clase)

La plantilla de clase describe un objeto que puede servir como una `CharType` faceta de configuración regional para controlar las conversiones de secuencias de valores de tipo a tiempo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Parámetros

*CharType*\
Tipo usado dentro de un programa para codificar caracteres.

*InputIterator*\
Iterador del que se leen los valores de hora.

## <a name="remarks"></a>Observaciones

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[time_get](#time_get)|Constructor para los objetos de tipo `time_get`.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|
|[iter_type](#iter_type)|Tipo que describe un iterador de entrada.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[date_order](#date_order)|Devuelve el orden de fecha utilizado por una faceta.|
|[do_date_order](#do_date_order)|Una función miembro virtual protegida a la que se llama para devolver el orden de fecha utilizado por una faceta.|
|[do_get](#do_get)|Lee y convierten datos de caracteres en un valor de hora.|
|[do_get_date](#do_get_date)|Una función miembro virtual protegida a la que se llama para analizar una cadena como la fecha generada por el especificador `x` para `strftime`.|
|[do_get_monthname](#do_get_monthname)|Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del mes.|
|[do_get_time](#do_get_time)|Una función miembro virtual protegida a la que se llama para analizar una cadena como la fecha generada por el especificador `X` para `strftime`.|
|[do_get_weekday](#do_get_weekday)|Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del día de la semana.|
|[do_get_year](#do_get_year)|Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del año.|
|[get](#get)|Lee de un origen de datos de caracteres y convierte estos datos en una hora que se almacena en un struct de hora.|
|[get_date](#get_date)|Analiza una cadena como la fecha generada por el especificador `x` para `strftime`.|
|[get_monthname](#get_monthname)|Analiza una cadena como el nombre del mes.|
|[get_time](#get_time)|Analiza una cadena como la fecha generada por el especificador `X` para `strftime`.|
|[get_weekday](#get_weekday)|Analiza una cadena como el nombre del día de la semana.|
|[get_year](#get_year)|Analiza una cadena como el nombre del año.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="time_getchar_type"></a><a name="char_type"></a>time_get::char_type

Tipo que se usa para describir un carácter empleado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla **CharType**.

## <a name="time_getdate_order"></a><a name="date_order"></a>time_get::date_order

Devuelve el orden de fecha utilizado por una faceta.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>Valor devuelto

El orden de fecha usado por una faceta.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [do_date_order](#do_date_order).

### <a name="example"></a>Ejemplo

```cpp
// time_get_date_order.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
void po( char *p )
{
   locale loc( p );

   time_get <char>::dateorder order = use_facet <time_get <char> >( loc ).date_order ( );
   cout << loc.name( );
   switch (order){
      case time_base::dmy: cout << "(day, month, year)" << endl;
      break;
      case time_base::mdy: cout << "(month, day, year)" << endl;
      break;
      case time_base::ydm: cout << "(year, day, month)" << endl;
      break;
      case time_base::ymd: cout << "(year, month, day)"<< endl;
      break;
      case time_base::no_order: cout << "(no_order)"<< endl;
      break;
   }
}

int main( )
{
   po( "C" );
   po( "german" );
   po( "English_Britain" );
}
```

```Output
C(month, day, year)
German_Germany.1252(day, month, year)
English_United Kingdom.1252(day, month, year)
```

## <a name="time_getdo_date_order"></a><a name="do_date_order"></a>time_get::do_date_order

Una función miembro virtual protegida a la que se llama para devolver el orden de fecha utilizado por una faceta.

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>Valor devuelto

El orden de fecha usado por una faceta.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida devuelve un valor de tipo **time_base::dateorder**, que describe el orden en el que [do_get_date](#do_get_date) compara los componentes de fecha. En esta implementación, el valor es **time_base::mdy**, que corresponde a las fechas con el formato Diciembre 2, 1979.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [date_order](#date_order), que llama a `do_date_order`.

## <a name="time_getdo_get"></a><a name="do_get"></a>time_get::do_get

Lee y convierten datos de caracteres en un valor de hora. Acepta un modificador y especificador de conversión.

```cpp
virtual iter_type
    do_get(
iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que indica el inicio de la secuencia que se va a convertir.

*Última*\
Iterador de entrada que indica el final de la secuencia.

*iosbase*\
Objeto de secuencia.

*Estado*\
Un campo en iosbase donde se establecen los elementos de máscara de bits adecuados para indicar errores.

*Ptm*\
Puntero a la estructura de tiempo en la que se debe almacenar la hora.

*Fmt*\
Carácter especificador de conversión.

*Mod*\
Carácter modificador opcional.

### <a name="return-value"></a>Valor devuelto

Devuelve un iterador que designa el primer elemento no convertido. Un error `ios_base::failbit` de `state` conversión se establece y devuelve *primero*.

### <a name="remarks"></a>Observaciones

La función miembro virtual convierte y omite uno o`first` `last`varios elementos de entrada en el `*pt`intervalo [ , ) para determinar los valores almacenados en uno o varios miembros de . Un error `ios_base::failbit` de `state` conversión se establece y devuelve *primero*. De lo contrario, la función devuelve un iterador que designa el primer elemento no convertido.

Los especificadores de conversión son:

`'a'` o `'A'`: se comporta igual que [time_get::get_weekday](#get_weekday).

`'b'`, `'B'` o `'h'`: se comporta igual que [time_get::get_monthname](#get_monthname).

`'c'`: se comporta igual que `"%b %d %H : %M : %S %Y"`.

`'C'`: convierte un campo de entrada decimal en el intervalo [0, 99] en el valor `val` y almacena `val * 100 - 1900` en `pt-&tm_year`.

`'d'` o `'e'`: convierte un campo de entrada decimal en el intervalo [1, 31] y almacena su valor en `pt-&tm_mday`.

`'D'`: se comporta igual que `"%m / %d / %y"`.

`'H'`: convierte un campo de entrada decimal en el intervalo [0, 23] y almacena su valor en `pt-&tm_hour`.

`'I'`: convierte un campo de entrada decimal en el intervalo [0, 11] y almacena su valor en `pt-&tm_hour`.

`'j'`: convierte un campo de entrada decimal en el intervalo [1, 366] y almacena su valor en `pt-&tm_yday`.

`'m'`: convierte un campo de entrada decimal en el intervalo [1, 12] en el valor `val` y almacena `val - 1` en y almacena su valor en `pt-&tm_mon`.

`'M'`: convierte un campo de entrada decimal en el intervalo [0, 59] y almacena su valor en `pt-&tm_min`.

`'n'` o `'t'`: se comporta igual que `" "`.

`'p'`: convierte “AM” o “am” en cero y “PM” o “pm” en 12 y agrega este valor a `pt-&tm_hour`.

`'r'`: se comporta igual que `"%I : %M : %S %p"`.

`'R'`: se comporta igual que `"%H %M"`.

`'S'`: convierte un campo de entrada decimal en el intervalo [0, 59] y almacena su valor en `pt-&tm_sec`.

`'T'` o `'X'`: se comporta igual que `"%H : %M : S"`.

`'U'`: convierte un campo de entrada decimal en el intervalo [0, 53] y almacena su valor en `pt-&tm_yday`.

`'w'`: convierte un campo de entrada decimal en el intervalo [0, 6] y almacena su valor en `pt-&tm_wday`.

`'W'`: convierte un campo de entrada decimal en el intervalo [0, 53] y almacena su valor en `pt-&tm_yday`.

`'x'`: se comporta igual que `"%d / %m / %y"`.

`'y'`: convierte un campo de entrada decimal en el intervalo [0, 99] en el valor `val` y almacena `val < 69  val + 100 : val` en `pt-&tm_year`.

`'Y'`: se comporta igual que [time_get::get_year](#get_year).

Cualquier otro especificador de conversión establece `ios_base::failbit` en `state` y devuelve. En esta implementación, ningún modificador tiene efecto alguno.

## <a name="time_getdo_get_date"></a><a name="do_get_date"></a>time_get::do_get_date

Una función miembro virtual protegida a la que se llama para analizar una cadena como la fecha generada por el especificador *x* para `strftime`.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*Última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

*iosbase*\
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

*Estado*\
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

*Ptm*\
Un puntero a donde se va a almacenar la información de fecha.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida intenta comparar los elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que reconoce un campo de entrada de fecha completo y que no esté vacío. Si se realiza correctamente, convierte este campo a su valor equivalente como los componentes **\_tm::tm mon**, `ptm->tm_mon` **tm::tm\_day**y **tm::tm\_year**, y almacena los resultados en , `ptm->tm_day`, y `ptm->tm_year`, respectivamente. Devuelve un iterador que designa el primer elemento más allá del campo de entrada de fecha. De lo contrario, la función se establece `iosbase::failbit` en *estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada de fecha válido. En cualquier caso, si el valor devuelto `ios_base::eofbit` es igual a *last*, la función se establece en *state*.

El formato para el campo de entrada de fecha depende de la configuración regional. Para la configuración regional predeterminada, el campo de entrada de fecha tiene el formato MMM DD, AAAA, donde:

- MMM coincide con una llamada a [get_monthname](#get_monthname), lo que proporciona el mes.

- DD es una secuencia de dígitos decimales cuyo valor numérico correspondiente debe estar en el intervalo [1, 31], lo que proporciona el día del mes.

- AAAA coincide con una llamada a [get_year](#get_year), lo que proporciona el año.

Los espacios y comas literales deben coincidir con los elementos correspondientes en la secuencia de entrada.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_date](#get_date), que llama a `do_get_date`.

## <a name="time_getdo_get_monthname"></a><a name="do_get_monthname"></a>time_get::do_get_monthname

Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del mes.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*Última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

*iosbase*\
Sin usar.

*Estado*\
Un parámetro de salida que establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

*Ptm*\
Un puntero a donde se va a almacenar la información del mes.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida intenta comparar los elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que reconoce un campo de entrada de mes completo y que no esté vacío. Si se realiza correctamente, convierte este campo a su valor equivalente como el `ptm->tm_mon`componente **tm::tm\_mon**y almacena el resultado en . Devuelve un iterador que designa el primer elemento más allá del campo de entrada de mes. De lo contrario, la función se establece `ios_base::failbit` en *estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada de mes válido. En cualquier caso, si el valor devuelto `ios_base::eofbit` es igual a *last*, la función se establece en *state*.

El campo de entrada del mes es una secuencia que coincide con el conjunto más largo de secuencias de configuración regional, como Ene., enero, Feb., febrero y así sucesivamente. El valor convertido es el número de meses desde enero.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_monthname](#get_monthname), que llama a `do_get_monthname`.

## <a name="time_getdo_get_time"></a><a name="do_get_time"></a>time_get::do_get_time

Una función miembro virtual protegida que se llama para *X* analizar una `strftime`cadena como la fecha producida por el especificador X para .

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*Última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

*iosbase*\
Sin usar.

*Estado*\
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

*Ptm*\
Un puntero a donde se va a almacenar la información de fecha.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida intenta comparar los elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que reconoce un campo de entrada de hora completo y que no esté vacío. Si se realiza correctamente, convierte este campo `tm::tm_hour`a `tm::tm_min`su `tm::tm_sec`valor equivalente como `ptm->tm_hour` `ptm->tm_min`componentes `ptm->tm_sec`, , y , y almacena los resultados en , , y , respectivamente. Devuelve un iterador que designa el primer elemento más allá del campo de entrada de hora. De lo contrario, la función se establece `ios_base::failbit` en *estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada de hora válido. En cualquier caso, si el valor devuelto `ios_base::eofbit` es igual a *last*, la función se establece en *state*.

En esta implementación, el campo de entrada de hora tiene el formato HH:MM:SS, donde:

- HH es una secuencia de dígitos decimales cuyo valor numérico correspondiente debe estar en el intervalo [0, 24], lo que proporciona la hora del día.

- MM es una secuencia de dígitos decimales cuyo valor numérico correspondiente debe estar en el intervalo [0, 60], lo que proporciona los minutos transcurridos de la hora.

- SS es una secuencia de dígitos decimales cuyo valor numérico correspondiente debe estar en el intervalo [0, 60], lo que proporciona los segundos transcurridos del minuto.

Los dos puntos literales deben coincidir con los elementos correspondientes en la secuencia de entrada.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_time](#get_time), que llama a `do_get_time`.

## <a name="time_getdo_get_weekday"></a><a name="do_get_weekday"></a>time_get::do_get_weekday

Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del día de la semana.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*Última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

*iosbase*\
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

*Estado*\
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

*Ptm*\
Un puntero a donde se va a almacenar la información del día de la semana.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro protegido virtual intenta hacer coincidir `first`los `last`elementos secuenciales que comienzan al *principio* en la secuencia [ , ) hasta que ha reconocido un campo de entrada de día de la semana completo y no vacío. Si se realiza correctamente, convierte este campo a su valor equivalente como el `ptm->tm_wday`componente **\_tm::tm wday**y almacena el resultado en . Devuelve un iterador que designa el primer elemento más allá del campo de entrada de día de la semana. De lo contrario, la función se establece `ios_base::failbit` en *estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada de día de la semana válido. En cualquier caso, si el valor devuelto `ios_base::eofbit` es igual a *last*, la función se establece en *state*.

El campo de entrada de día de la semana es una secuencia que coincide con el conjunto más largo de secuencias de configuración regional, como Dom., domingo. Lun., lunes y así sucesivamente. El valor convertido es el número de días desde el domingo.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_weekday](#get_weekday), que llama a `do_get_weekday`.

## <a name="time_getdo_get_year"></a><a name="do_get_year"></a>time_get::do_get_year

Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del año.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*Última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

*iosbase*\
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

*Estado*\
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

*Ptm*\
Un puntero a donde se va a almacenar la información de año.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro protegido virtual intenta hacer coincidir `first`los `last`elementos secuenciales que comienzan al *principio* en la secuencia [ , ) hasta que ha reconocido un campo de entrada de año completo y no vacío. Si se realiza correctamente, convierte este campo a su valor equivalente como el `ptm->tm_year`componente **tm::tm\_year**y almacena el resultado en . Devuelve un iterador que designa el primer elemento más allá del campo de entrada de año. De lo contrario, la función se establece `ios_base::failbit` en *estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada de año válido. En cualquier caso, si el valor devuelto `ios_base::eofbit` es igual a *last*, la función se establece en *state*.

El campo de entrada de año es una secuencia de dígitos decimales cuyo valor numérico correspondiente debe estar en el intervalo [1900, 2036]. El valor almacenado es este valor menos 1900. En esta implementación, los valores en el intervalo [69, 136) representan el intervalo de años [1969, 2036). Los valores del intervalo [0, 69) también son posibles, pero pueden representar el intervalo de años [1900, 1969) o [2000, 2069), según el entorno de traducción específico.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_year](#get_year), que llama a `do_get_year`.

## <a name="time_getget"></a><a name="get"></a>time_get::get

Lee de un origen de datos de caracteres y convierte estos datos en una hora que se almacena en un struct de hora. La primera función acepta un especificador y modificador de conversión y la segunda acepta varios.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char_type* fmt_first,
    char_type* fmt_last) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que indica dónde comienza la secuencia que se va a convertir.

*Última*\
Iterador de entrada que indica dónde acaba la secuencia que se va a convertir.

*iosbase*\
Flujo.

*Estado*\
Se establecen los elementos de máscara de bits apropiados para que el estado de la secuencia indique los errores.

*Ptm*\
Puntero a la estructura de tiempo en la que se va a almacenar la hora.

*Fmt*\
Carácter especificador de conversión.

*Mod*\
Carácter modificador opcional.

*fmt_first*\
Apunta al principio de las directivas de formato.

*fmt_last*\
Apunta al final de las directivas de formato.

### <a name="return-value"></a>Valor devuelto

Devuelve un iterador al primer carácter después `*ptm`de los datos que se usaron para asignar la estructura de tiempo .

### <a name="remarks"></a>Observaciones

La primera función miembro devuelve `do_get(first, last, iosbase, state, ptm, fmt, mod)`.

La segunda función miembro llama a `do_get` bajo el control del formato delimitado por `[fmt_first, fmt_last)`. Trata el formato como una secuencia de campos, donde cada uno de ellos determina la conversión de cero o más elementos de entrada delimitados por `[first, last)`. Devuelve un iterador que designa el primer elemento no convertido. Hay tres tipos de campos:

A por ciento (%) en el formato, seguido de un modificador opcional *mod* en el conjunto [EOQ-], seguido de `do_get(first, last, iosbase, state, ptm, fmt, mod)`un especificador de conversión *fmt*, reemplaza *primero* por el valor devuelto por . Un error `ios_base::failbit` de conversión se establece en *estado* y devuelve.

Un elemento de espacio en blanco en el formato omite el elemento cero o más elementos de espacio en blanco de entrada.

Cualquier otro elemento en el formato debe coincidir con el siguiente elemento de entrada, que se omite. Un error `ios_base::failbit` de coincidencia se establece en *estado* y devuelve.

## <a name="time_getget_date"></a><a name="get_date"></a>time_get::get_date

Analiza una cadena como la fecha generada por el especificador *x* para `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*Última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

*iosbase*\
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

*Estado*\
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

*Ptm*\
Un puntero a donde se va a almacenar la información de fecha.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro `last`devuelve `iosbase` `state` [do_get_date](#do_get_date)(`first`, , , , . `ptm`. .

Tenga en cuenta que los meses se cuentan de 0 a 11.

### <a name="example"></a>Ejemplo

```cpp
// time_get_get_date.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset(&t, 0, sizeof(struct tm));

   pszGetF << "July 4, 2000";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get<char> >
   (loc).get_date(basic_istream<char>::_Iter(pszGetF.rdbuf( ) ),
            basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if ( st & ios_base::failbit )
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(July 4, 2000) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 4
tm_mon: 6
tm_year: 100
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="time_getget_monthname"></a><a name="get_monthname"></a>time_get::get_monthname

Analiza una cadena como el nombre del mes.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*Última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

*iosbase*\
Sin usar.

*Estado*\
Un parámetro de salida que establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

*Ptm*\
Un puntero a donde se va a almacenar la información del mes.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro `last`devuelve `iosbase` `state` [do_get_monthname](#do_get_monthname)(`first`, , , , . `ptm`. .

### <a name="example"></a>Ejemplo

```cpp
// time_get_get_monthname.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "juillet";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get <char> >
   (loc).get_monthname(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
              basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(juillet) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 0
tm_mon: 6
tm_year: 0
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="time_getget_time"></a><a name="get_time"></a>time_get::get_time

Analiza una cadena como la fecha *X* producida por `strftime`el especificador X para .

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*Última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

*iosbase*\
Sin usar.

*Estado*\
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

*Ptm*\
Un puntero a donde se va a almacenar la información de fecha.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro `last`devuelve `iosbase` `state` [do_get_time](#do_get_time)(`first`, , , , . `ptm`. .

### <a name="example"></a>Ejemplo

```cpp
// time_get_get_time.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "11:13:20";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get <char> >
      (loc).get_time(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << endl;
}
```

```Output
time_get::get_time(11:13:20) =
tm_sec: 20
tm_min: 13
tm_hour: 11
```

## <a name="time_getget_weekday"></a><a name="get_weekday"></a>time_get::get_weekday

Analiza una cadena como el nombre del día de la semana.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*Última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

*iosbase*\
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

*Estado*\
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

*Ptm*\
Un puntero a donde se va a almacenar la información del día de la semana.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro `last`devuelve `iosbase` `state` [do_get_weekday](#do_get_weekday)(`first`, , , , . `ptm`. .

### <a name="example"></a>Ejemplo

```cpp
// time_get_get_weekday.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "mercredi";
   pszGetF.imbue(loc);
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_weekday(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_wday: " << t.tm_wday
      << endl;
}
```

```Output
time_get::get_time(mercredi) =
tm_wday: 3
```

## <a name="time_getget_year"></a><a name="get_year"></a>time_get::get_year

Analiza una cadena como el nombre del año.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*Última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

*iosbase*\
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

*Estado*\
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

*Ptm*\
Un puntero a donde se va a almacenar la información de año.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro `last`devuelve `iosbase` `state` [do_get_year](#do_get_year)(`first`, , , , . `ptm`. ).

### <a name="example"></a>Ejemplo

```cpp
// time_get_get_year.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "1928";

   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_year(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_year: " << t.tm_year
      << endl;
}
```

```Output
time_get::get_year(1928) =
tm_year: 28
```

## <a name="time_getiter_type"></a><a name="iter_type"></a>time_get::iter_type

Tipo que describe un iterador de entrada.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla **InputIterator**.

## <a name="time_gettime_get"></a><a name="time_get"></a>time_get::time_get

Constructor para los objetos de tipo `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Parámetros

*Árbitros*\
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

### <a name="remarks"></a>Observaciones

Los valores posibles para el parámetro *refs* y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \>1: Estos valores no están definidos.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa su objeto base con`refs` **locale::**[faceta](../standard-library/locale-class.md#facet_class)( ).

## <a name="see-also"></a>Consulte también

[\<>de la localidad](../standard-library/locale.md)\
[Clase time_base](../standard-library/time-base-class.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
