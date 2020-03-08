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
ms.openlocfilehash: e605423b829305bd1e7bde8be4fdbf312c8ce3c1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876196"
---
# <a name="time_get-class"></a>time_get (Clase)

La plantilla de clase describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de secuencias de tipo `CharType` a valores de hora.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Parámetros

\ *CharType*
Tipo usado dentro de un programa para codificar caracteres.

\ *InputIterator*
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

**Encabezado:** \<configuración regional >

**Espacio de nombres:** std

## <a name="char_type"></a>  time_get::char_type

Tipo que se usa para describir un carácter empleado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla **CharType**.

## <a name="date_order"></a>  time_get::date_order

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

## <a name="do_date_order"></a>  time_get::do_date_order

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

## <a name="do_get"></a>  time_get::do_get

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

*primer*\
Iterador de entrada que indica el inicio de la secuencia que se va a convertir.

*última*\
Iterador de entrada que indica el final de la secuencia.

\ *iosbase*
Objeto de secuencia.

\ de *Estado*
Campo de iosbase donde se establecen los elementos de máscara de máscara adecuados para indicar errores.

\ *PTM*
Puntero a la estructura de tiempo en la que se debe almacenar la hora.

*fmt*\
Carácter especificador de conversión.

\ *mod*
Carácter modificador opcional.

### <a name="return-value"></a>Valor devuelto

Devuelve un iterador que designa el primer elemento no convertido. Un error de conversión establece `ios_base::failbit` en `state` y devuelve en *primer lugar*.

### <a name="remarks"></a>Observaciones

La función miembro virtual convierte y omite uno o varios elementos de entrada en el intervalo [`first`, `last`) para determinar los valores almacenados en uno o varios miembros de `*pt`. Un error de conversión establece `ios_base::failbit` en `state` y devuelve en *primer lugar*. De lo contrario, la función devuelve un iterador que designa el primer elemento no convertido.

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

## <a name="do_get_date"></a>  time_get::do_get_date

Una función miembro virtual protegida a la que se llama para analizar una cadena como la fecha generada por el especificador *x* para `strftime`.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

\ *iosbase*
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

\ de *Estado*
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

\ *PTM*
Un puntero a donde se va a almacenar la información de fecha.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida intenta comparar los elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que reconoce un campo de entrada de fecha completo y que no esté vacío. Si se realiza correctamente, convierte este campo en su valor equivalente como los componentes **TM:: tm\_Mon**, **TM:: TM\_Day**y **TM:: TM\_Year**, y almacena los resultados en `ptm->tm_mon`, `ptm->tm_day`y `ptm->tm_year`, respectivamente. Devuelve un iterador que designa el primer elemento más allá del campo de entrada de fecha. De lo contrario, la función establece `iosbase::failbit` en el *Estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada de fecha válido. En cualquier caso, si el valor devuelto es igual a *Last*, la función establece `ios_base::eofbit` en el *Estado*.

El formato para el campo de entrada de fecha depende de la configuración regional. Para la configuración regional predeterminada, el campo de entrada de fecha tiene el formato MMM DD, AAAA, donde:

- MMM coincide con una llamada a [get_monthname](#get_monthname), lo que proporciona el mes.

- DD es una secuencia de dígitos decimales cuyo valor numérico correspondiente debe estar en el intervalo [1, 31], lo que proporciona el día del mes.

- AAAA coincide con una llamada a [get_year](#get_year), lo que proporciona el año.

Los espacios y comas literales deben coincidir con los elementos correspondientes en la secuencia de entrada.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_date](#get_date), que llama a `do_get_date`.

## <a name="do_get_monthname"></a>  time_get::do_get_monthname

Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del mes.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

\ *iosbase*
Sin usar.

\ de *Estado*
Un parámetro de salida que establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

\ *PTM*
Un puntero a donde se va a almacenar la información del mes.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida intenta comparar los elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que reconoce un campo de entrada de mes completo y que no esté vacío. Si se realiza correctamente, convierte este campo en su valor equivalente como el componente **TM:: tm\_Mon**y almacena el resultado en `ptm->tm_mon`. Devuelve un iterador que designa el primer elemento más allá del campo de entrada de mes. De lo contrario, la función establece `ios_base::failbit` en el *Estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada de mes válido. En cualquier caso, si el valor devuelto es igual a *Last*, la función establece `ios_base::eofbit` en el *Estado*.

El campo de entrada del mes es una secuencia que coincide con el conjunto más largo de secuencias de configuración regional, como Ene., enero, Feb., febrero y así sucesivamente. El valor convertido es el número de meses desde enero.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_monthname](#get_monthname), que llama a `do_get_monthname`.

## <a name="do_get_time"></a>  time_get::do_get_time

Una función miembro virtual protegida a la que se llama para analizar una cadena como la fecha generada por el especificador *X* para `strftime`.

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

\ *iosbase*
Sin usar.

\ de *Estado*
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

\ *PTM*
Un puntero a donde se va a almacenar la información de fecha.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida intenta comparar los elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que reconoce un campo de entrada de hora completo y que no esté vacío. Si se realiza correctamente, convierte este campo en su valor equivalente como los componentes `tm::tm_hour`, `tm::tm_min`y `tm::tm_sec`, y almacena los resultados en `ptm->tm_hour`, `ptm->tm_min`y `ptm->tm_sec`, respectivamente. Devuelve un iterador que designa el primer elemento más allá del campo de entrada de hora. De lo contrario, la función establece `ios_base::failbit` en el *Estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada de hora válido. En cualquier caso, si el valor devuelto es igual a *Last*, la función establece `ios_base::eofbit` en el *Estado*.

En esta implementación, el campo de entrada de hora tiene el formato HH:MM:SS, donde:

- HH es una secuencia de dígitos decimales cuyo valor numérico correspondiente debe estar en el intervalo [0, 24], lo que proporciona la hora del día.

- MM es una secuencia de dígitos decimales cuyo valor numérico correspondiente debe estar en el intervalo [0, 60], lo que proporciona los minutos transcurridos de la hora.

- SS es una secuencia de dígitos decimales cuyo valor numérico correspondiente debe estar en el intervalo [0, 60], lo que proporciona los segundos transcurridos del minuto.

Los dos puntos literales deben coincidir con los elementos correspondientes en la secuencia de entrada.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_time](#get_time), que llama a `do_get_time`.

## <a name="do_get_weekday"></a>  time_get::do_get_weekday

Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del día de la semana.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

\ *iosbase*
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

\ de *Estado*
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

\ *PTM*
Un puntero a donde se va a almacenar la información del día de la semana.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida intenta comparar los elementos secuenciales a partir de la *primera* de la secuencia [`first`, `last`) hasta que reconoce un campo de entrada de día de la semana completo y que no esté vacío. Si se realiza correctamente, convierte este campo en su valor equivalente como el componente **TM:: tm\_wday**y almacena el resultado en `ptm->tm_wday`. Devuelve un iterador que designa el primer elemento más allá del campo de entrada de día de la semana. De lo contrario, la función establece `ios_base::failbit` en el *Estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada de día de la semana válido. En cualquier caso, si el valor devuelto es igual a *Last*, la función establece `ios_base::eofbit` en el *Estado*.

El campo de entrada de día de la semana es una secuencia que coincide con el conjunto más largo de secuencias de configuración regional, como Dom., domingo. Lun., lunes y así sucesivamente. El valor convertido es el número de días desde el domingo.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_weekday](#get_weekday), que llama a `do_get_weekday`.

## <a name="do_get_year"></a>  time_get::do_get_year

Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del año.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

\ *iosbase*
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

\ de *Estado*
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

\ *PTM*
Un puntero a donde se va a almacenar la información de año.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida intenta comparar los elementos secuenciales a partir de la *primera* de la secuencia [`first`, `last`) hasta que reconoce un campo de entrada de año completo y que no esté vacío. Si se realiza correctamente, convierte este campo en su valor equivalente como el componente **TM:: tm\_Year**y almacena el resultado en `ptm->tm_year`. Devuelve un iterador que designa el primer elemento más allá del campo de entrada de año. De lo contrario, la función establece `ios_base::failbit` en el *Estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de campo de entrada de año válido. En cualquier caso, si el valor devuelto es igual a *Last*, la función establece `ios_base::eofbit` en el *Estado*.

El campo de entrada de año es una secuencia de dígitos decimales cuyo valor numérico correspondiente debe estar en el intervalo [1900, 2036]. El valor almacenado es este valor menos 1900. En esta implementación, los valores en el intervalo [69, 136) representan el intervalo de años [1969, 2036). Los valores del intervalo [0, 69) también son posibles, pero pueden representar el intervalo de años [1900, 1969) o [2000, 2069), según el entorno de traducción específico.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_year](#get_year), que llama a `do_get_year`.

## <a name="get"></a>  time_get::get

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

*primer*\
Iterador de entrada que indica dónde comienza la secuencia que se va a convertir.

*última*\
Iterador de entrada que indica dónde acaba la secuencia que se va a convertir.

\ *iosbase*
Flujo.

\ de *Estado*
Se establecen los elementos de máscara de bits apropiados para que el estado de la secuencia indique los errores.

\ *PTM*
Puntero a la estructura de tiempo en la que se va a almacenar la hora.

*fmt*\
Carácter especificador de conversión.

\ *mod*
Carácter modificador opcional.

*fmt_first*\
Apunta al principio de las directivas de formato.

*fmt_last*\
Apunta al final de las directivas de formato.

### <a name="return-value"></a>Valor devuelto

Devuelve un iterador al primer carácter después de los datos que se usaron para asignar la estructura de tiempo `*ptm`.

### <a name="remarks"></a>Observaciones

La primera función miembro devuelve `do_get(first, last, iosbase, state, ptm, fmt, mod)`.

La segunda función miembro llama a `do_get` bajo el control del formato delimitado por `[fmt_first, fmt_last)`. Trata el formato como una secuencia de campos, donde cada uno de ellos determina la conversión de cero o más elementos de entrada delimitados por `[first, last)`. Devuelve un iterador que designa el primer elemento no convertido. Hay tres tipos de campos:

Un por ciento (%) en el formato, seguido de un modificador opcional *mod* en el conjunto [CEO #], seguido de un especificador de conversión *FMT*, reemplaza *primero* por el valor devuelto por `do_get(first, last, iosbase, state, ptm, fmt, mod)`. Un error de conversión establece `ios_base::failbit` en el *Estado* y devuelve.

Un elemento de espacio en blanco en el formato omite el elemento cero o más elementos de espacio en blanco de entrada.

Cualquier otro elemento en el formato debe coincidir con el siguiente elemento de entrada, que se omite. Un error de coincidencia establece `ios_base::failbit` en el *Estado* y devuelve.

## <a name="get_date"></a>  time_get::get_date

Analiza una cadena como la fecha generada por el especificador *x* para `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

\ *iosbase*
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

\ de *Estado*
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

\ *PTM*
Un puntero a donde se va a almacenar la información de fecha.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [do_get_date](#do_get_date)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="get_monthname"></a>  time_get::get_monthname

Analiza una cadena como el nombre del mes.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

\ *iosbase*
Sin usar.

\ de *Estado*
Un parámetro de salida que establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

\ *PTM*
Un puntero a donde se va a almacenar la información del mes.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [do_get_monthname](#do_get_monthname)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="get_time"></a>  time_get::get_time

Analiza una cadena como la fecha generada por el especificador *X* para `strftime`.

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

\ *iosbase*
Sin usar.

\ de *Estado*
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

\ *PTM*
Un puntero a donde se va a almacenar la información de fecha.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [do_get_time](#do_get_time)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="get_weekday"></a>  time_get::get_weekday

Analiza una cadena como el nombre del día de la semana.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

\ *iosbase*
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

\ de *Estado*
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

\ *PTM*
Un puntero a donde se va a almacenar la información del día de la semana.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [do_get_weekday](#do_get_weekday)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="get_year"></a>  time_get::get_year

Analiza una cadena como el nombre del año.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que se dirige al principio de la secuencia que se va a convertir.

*última*\
Iterador de entrada que se dirige al final de la secuencia que se va a convertir.

\ *iosbase*
Un formato de marca que cuando está establecido indica que el símbolo de moneda es opcional. De lo contrario, es obligatorio.

\ de *Estado*
Establece los elementos de máscara de bits apropiados para el estado de la secuencia en función de si las operaciones se realizaron correctamente.

\ *PTM*
Un puntero a donde se va a almacenar la información de año.

### <a name="return-value"></a>Valor devuelto

Un iterador de entrada que se dirige al primer elemento más allá del campo de entrada.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [do_get_year](#do_get_year)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="iter_type"></a>  time_get::iter_type

Tipo que describe un iterador de entrada.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla **InputIterator**.

## <a name="time_get"></a>  time_get::time_get

Constructor para los objetos de tipo `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Parámetros

\ *Refs*
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

### <a name="remarks"></a>Observaciones

Los valores posibles para el parámetro *Refs* y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \> 1: estos valores no están definidos.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa su objeto base con **locale::** [facet](../standard-library/locale-class.md#facet_class)(`refs`).

## <a name="see-also"></a>Consulte también

[\<locale>](../standard-library/locale.md)\
[time_base (Clase)](../standard-library/time-base-class.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
