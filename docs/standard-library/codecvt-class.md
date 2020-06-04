---
title: codecvt (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt
- xlocale/std::codecvt::extern_type
- xlocale/std::codecvt::intern_type
- xlocale/std::codecvt::state_type
- xlocale/std::codecvt::always_noconv
- xlocale/std::codecvt::do_always_noconv
- xlocale/std::codecvt::do_encoding
- xlocale/std::codecvt::do_in
- xlocale/std::codecvt::do_length
- xlocale/std::codecvt::do_max_length
- xlocale/std::codecvt::do_out
- xlocale/std::codecvt::do_unshift
- xlocale/std::codecvt::encoding
- xlocale/std::codecvt::in
- xlocale/std::codecvt::length
- xlocale/std::codecvt::max_length
- xlocale/std::codecvt::out
- xlocale/std::codecvt::unshift
helpviewer_keywords:
- std::codecvt [C++]
- std::codecvt [C++], extern_type
- std::codecvt [C++], intern_type
- std::codecvt [C++], state_type
- std::codecvt [C++], always_noconv
- std::codecvt [C++], do_always_noconv
- std::codecvt [C++], do_encoding
- std::codecvt [C++], do_in
- std::codecvt [C++], do_length
- std::codecvt [C++], do_max_length
- std::codecvt [C++], do_out
- std::codecvt [C++], do_unshift
- std::codecvt [C++], encoding
- std::codecvt [C++], in
- std::codecvt [C++], length
- std::codecvt [C++], max_length
- std::codecvt [C++], out
- std::codecvt [C++], unshift
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
ms.openlocfilehash: 3dba971b112c23325e0529e53746cbee827df5e9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371949"
---
# <a name="codecvt-class"></a>codecvt (Clase)

Plantilla de clase que describe un objeto que puede servir como faceta de configuración regional. Puede controlar las conversiones entre una secuencia de valores usados para codificar caracteres dentro del programa y una secuencia de valores usados para codificar caracteres fuera del programa.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Parámetros

*CharType*\
Tipo usado dentro de un programa para codificar caracteres.

*Byte*\
Tipo usado para codificar caracteres fuera de un programa.

*StateType*\
Tipo que se puede usar para representar los estados intermedios de una conversión entre los tipos internos y externos de representaciones de caracteres.

## <a name="remarks"></a>Observaciones

La plantilla de clase describe un objeto que puede servir como [una faceta de configuración regional,](../standard-library/locale-class.md#facet_class)para controlar las conversiones entre una secuencia de valores de tipo *CharType* y una secuencia de valores de tipo *Byte*. La clase *StateType* caracteriza la transformación y un objeto de clase *StateType* almacena toda la información de estado necesaria durante una conversión.

La codificación interna utiliza una representación con un número fijo de bytes por carácter, normalmente tipo **char** o tipo **wchar_t**.

Como ocurre con cualquier faceta de configuración regional, el `id` de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en `id`.

Las versiones de plantilla de [do_in](#do_in) y [do_out](#do_out) siempre devuelven `codecvt_base::noconv`.

La biblioteca estándar de C++ define varias especializaciones explícitas:

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

convierte entre secuencias **de wchar_t** y **char.**

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

convierte entre `char16_t` secuencias codificadas como secuencias UTF-16 y **char** codificadas como UTF-8.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

convierte entre `char32_t` secuencias codificadas como UTF-32 (UCS-4) y secuencias **char** codificadas como UTF-8.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[codecvt](#codecvt)|Constructor de objetos de clase `codecvt` que actúa como faceta de configuración regional para controlar las conversiones.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[extern_type](#extern_type)|Tipo de carácter que se usa para las representaciones externas.|
|[intern_type](#intern_type)|Tipo de carácter que se usa para las representaciones internas.|
|[state_type](#state_type)|Tipo de carácter que se usa para representar los estados intermedios durante las conversiones entre las representaciones internas y externas.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[always_noconv](#always_noconv)|Comprueba si no es necesario realizar ninguna conversión.|
|[do_always_noconv](#do_always_noconv)|Función virtual a la que se llama para comprobar si no es necesario realizar ninguna conversión.|
|[do_encoding](#do_encoding)|Función virtual que comprueba si `Byte` la codificación de la `Byte` secuencia depende `CharType` del estado, si la relación entre los valores utilizados y los valores generados es constante y, si es así, determina el valor de esa proporción.|
|[do_in](#do_in)|Una función virtual llamada para `Byte` convertir una secuencia `CharType` de valores internos en una secuencia de valores externos.|
|[do_length](#do_length)|Una función virtual que `Byte` determina cuántos valores `Byte` de una secuencia determinada de `CharType` valores externos producen `Byte` no más de un número determinado de valores internos y devuelve ese número de valores.|
|[do_max_length](#do_max_length)|Función virtual que devuelve el número máximo de bytes externos necesarios para generar un `CharType` interno.|
|[do_out](#do_out)|Una función virtual llamada para `CharType` convertir una secuencia de valores internos en una secuencia de bytes externos.|
|[do_unshift](#do_unshift)|Una función virtual `Byte` llamada para proporcionar los valores necesarios en una `Byte` conversión dependiente del estado para completar el último carácter de una secuencia de valores.|
|[Codificación](#encoding)|Comprueba si la `Byte` codificación de la secuencia depende `Byte` del estado, si la relación entre los valores utilizados y los `CharType` valores generados es constante y, si es así, determina el valor de esa proporción.|
|[En](#in)|Convierte una representación externa `Byte` de una secuencia de valores `CharType` en una representación interna de una secuencia de valores.|
|[length](#length)|Determina cuántos `Byte` valores de una `Byte` secuencia determinada de valores externos `CharType` producen no más `Byte` de un número determinado de valores internos y devuelve ese número de valores.|
|[max_length](#max_length)|Devuelve el número `Byte` máximo de valores `CharType`externos necesarios para producir un archivo .|
|[hacia fuera](#out)|Convierte una secuencia `CharType` de valores internos `Byte` en una secuencia de valores externos.|
|[unshift](#unshift)|Proporciona los `Byte` valores externos necesarios en una conversión dependiente `Byte` del estado para completar el último carácter de la secuencia de valores.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="codecvtalways_noconv"></a><a name="always_noconv"></a>codecvt::always_noconv

Comprueba si no es necesario realizar conversiones.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Valor devuelto

Un valor booleano que es **true** si no es necesario realizar conversiones; **falso** si al menos uno necesita ser hecho.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [do_always_noconv](#do_always_noconv).

### <a name="example"></a>Ejemplo

```cpp
// codecvt_always_noconv.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result1 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;

   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result2 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;
}
```

```Output
No conversion is needed.
At least one conversion is required.
```

## <a name="codecvtcodecvt"></a><a name="codecvt"></a>codecvt::codecvt

Constructor de objetos de clase codecvt que actúa como faceta de configuración regional para controlar las conversiones.

```cpp
explicit codecvt(size_t refs = 0);
```

### <a name="parameters"></a>Parámetros

*Árbitros*\
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

### <a name="remarks"></a>Observaciones

Los valores posibles para el parámetro *refs* y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- 2: Estos valores no están definidos.

El constructor inicializa `locale::facet` su objeto base con [locale::facet](../standard-library/locale-class.md#facet_class)`(refs)`.

## <a name="codecvtdo_always_noconv"></a><a name="do_always_noconv"></a>codecvt::do_always_noconv

Una función virtual llamada para probar si no es necesario realizar conversiones.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Valor devuelto

La función miembro virtual protegida devuelve **true** solo `noconv`si cada llamada a [do_in](#do_in) o [do_out](#do_out) devuelve .

La versión de plantilla devuelve siempre **True**.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [always_noconv](#always_noconv), que llama a `do_always_noconv`.

## <a name="codecvtdo_encoding"></a><a name="do_encoding"></a>codecvt::do_encoding

Función virtual que comprueba si `Byte` la codificación de la `Byte` secuencia depende `CharType` del estado, si la relación entre los valores utilizados y los valores generados es constante y, si es así, determina el valor de esa proporción.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Valor devuelto

La función miembro virtual protegida devuelve:

- -1, si la codificación `extern_type` de secuencias de tipo depende del estado.

- 0, si la codificación implica secuencias de longitud variable.

- *N*, si la codificación solo implica secuencias de longitud *N*

### <a name="example"></a>Ejemplo

Vea el ejemplo de [encoding](#encoding), que llama a `do_encoding`.

## <a name="codecvtdo_in"></a><a name="do_in"></a>codecvt::do_in

Una función virtual llamada para `Byte` convertir una secuencia `CharType` de valores externos en una secuencia de valores internos.

```cpp
virtual result do_in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parámetros

*Estado*\
El estado de conversión que se mantiene entre las llamadas a la función miembro.

*first1*\
Puntero al principio de la secuencia que se va a convertir.

*last1*\
Puntero al final de la secuencia que se va a convertir.

*next1*\
Puntero más allá del final de la secuencia convertida, al primer carácter sin convertir.

*first2*\
Puntero al principio de la secuencia convertida.

*last2*\
Puntero al final de la secuencia convertida.

*next2*\
Puntero a `CharType` la que viene `CharType`después de la última convertida, al primer carácter inalterado de la secuencia de destino.

### <a name="return-value"></a>Valor devuelto

Un valor devuelto que indica si la operación se ha realizado correctamente, parcialmente o no se ha realizado correctamente. La función devuelve:

- `codecvt_base::error`si la secuencia de origen está mal formada.

- `codecvt_base::noconv` si la función no realiza ninguna conversión.

- `codecvt_base::ok`si la conversión tiene éxito.

- `codecvt_base::partial`si el origen es insuficiente o si el destino no es lo suficientemente grande, para que la conversión se realice correctamente.

### <a name="remarks"></a>Observaciones

*estado* debe representar el estado de conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. De lo contrario, su valor almacenado no se especifica.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [in](#in), que llama a `do_in`.

## <a name="codecvtdo_length"></a><a name="do_length"></a>codecvt::do_length

Una función virtual que `Byte` determina cuántos valores `Byte` de una secuencia determinada de `CharType` valores externos producen `Byte` no más de un número determinado de valores internos y devuelve ese número de valores.

```cpp
virtual int do_length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parámetros

*Estado*\
El estado de conversión que se mantiene entre las llamadas a la función miembro.

*first1*\
Puntero al principio de la secuencia externa.

*last1*\
Puntero al final de la secuencia externa.

*len2*\
El número `Byte` máximo de valores que puede devolver la función miembro.

### <a name="return-value"></a>Valor devuelto

Entero que representa un recuento del número máximo de conversiones, no mayor que *len2*, definido por la secuencia de origen externa en [ `first1`, `last1`).

### <a name="remarks"></a>Observaciones

La función miembro `do_in( state, first1, last1, next1, buf, buf + len2, next2)` virtual protegida llama eficazmente al `buf` *estado* (una copia del estado), a algunos búfer y punteros `next1` y `next2`.

Después, devuelve `next2` - `buf`. Por lo tanto, cuenta el número máximo de conversiones, no mayor `first1`que `last1` *len2*, definido por la secuencia de origen en [ , ).

La versión de plantilla siempre devuelve el menor de *last1* - *first1* y *len2*.

### <a name="example"></a>Ejemplo

Vea el [length](#length)ejemplo de `do_length`longitud , que llama a .

## <a name="codecvtdo_max_length"></a><a name="do_max_length"></a>codecvt::do_max_length

Función virtual que devuelve el `Byte` número máximo de `CharType`valores externos necesarios para producir un archivo interno.

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Valor devuelto

El número `Byte` máximo de valores `CharType`necesarios para producir uno .

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida devuelve el valor permitido más grande que puede devolver [do_length](#do_length) `( first1, last1, 1)` para los valores válidos arbitrarios de *first1* y *last1*.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [max_length](#max_length), que llama a `do_max_length`.

## <a name="codecvtdo_out"></a><a name="do_out"></a>codecvt::do_out

Una función virtual llamada para `CharType` convertir una secuencia `Byte` de valores internos en una secuencia de valores externos.

```cpp
virtual result do_out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parámetros

*Estado*\
El estado de conversión que se mantiene entre las llamadas a la función miembro.

*first1*\
Puntero al principio de la secuencia que se va a convertir.

*last1*\
Puntero al final de la secuencia que se va a convertir.

*next1*\
Referencia a un puntero al `CharType`primer no `CharType` convertido , después de la última conversión.

*first2*\
Puntero al principio de la secuencia convertida.

*last2*\
Puntero al final de la secuencia convertida.

*next2*\
Referencia a un puntero al `Byte`primer no `Byte` convertido , después de la última conversión.

### <a name="return-value"></a>Valor devuelto

La función devuelve:

- `codecvt_base::error`si la secuencia de origen está mal formada.

- `codecvt_base::noconv` si la función no realiza ninguna conversión.

- `codecvt_base::ok`si la conversión tiene éxito.

- `codecvt_base::partial`si el origen es insuficiente o si el destino no es lo suficientemente grande como para que la conversión se realice correctamente.

### <a name="remarks"></a>Observaciones

*estado* debe representar el estado de conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. De lo contrario, su valor almacenado no se especifica.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [out](#out), que llama a `do_out`.

## <a name="codecvtdo_unshift"></a><a name="do_unshift"></a>codecvt::do_unshift

Una función virtual `Byte` llamada para proporcionar los valores necesarios en una `Byte` conversión dependiente del estado para completar el último carácter de una secuencia de valores.

```cpp
virtual result do_unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parámetros

*Estado*\
El estado de conversión que se mantiene entre las llamadas a la función miembro.

*first2*\
Puntero a la primera posición del intervalo de destino.

*last2*\
Puntero a la última posición del intervalo de destino.

*next2*\
Puntero al primer elemento sin modificaciones en la secuencia de destino.

### <a name="return-value"></a>Valor devuelto

La función devuelve:

- `codecvt_base::error`si *el estado* representa un estado no válido

- `codecvt_base::noconv` si la función no realiza ninguna conversión

- `codecvt_base::ok`si la conversión tiene éxito

- `codecvt_base::partial`si el destino no es lo suficientemente grande como para que la conversión tenga éxito

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida `CharType`intenta convertir el elemento de origen `first2`(0) en una secuencia de destino que almacena dentro de [ , `last2`), excepto para el elemento `Byte`de terminación (0). Siempre almacena en *next2* un puntero al primer elemento inalterado de la secuencia de destino.

_ *State* debe representar el estado de conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. Normalmente, la conversión `CharType`del elemento de origen (0) deja el estado actual en el estado de conversión inicial.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [unshift](#unshift), que llama a `do_unshift`.

## <a name="codecvtencoding"></a><a name="encoding"></a>codecvt::encoding

Comprueba si la `Byte` codificación de la secuencia depende `Byte` del estado, si la relación entre los valores utilizados y los `CharType` valores generados es constante y, si es así, determina el valor de esa proporción.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto es positivo, ese `Byte` valor es `CharType` el número constante de caracteres necesarios para producir el carácter.

La función miembro virtual protegida devuelve:

- -1, si la codificación `extern_type` de secuencias de tipo depende del estado.

- 0, si la codificación implica secuencias de longitud variable.

- *N*, si la codificación implica solo secuencias de longitud *N.*

### <a name="remarks"></a>Observaciones

La función miembro devuelve [do_encoding](#do_encoding).

### <a name="example"></a>Ejemplo

```cpp
// codecvt_encoding.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
}
```

```Output
1
1
1
```

## <a name="codecvtextern_type"></a><a name="extern_type"></a>codecvt::extern_type

Tipo de carácter que se usa para las representaciones externas.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `Byte`.

## <a name="codecvtin"></a><a name="in"></a>codecvt::in

Convierte una representación externa `Byte` de una secuencia de valores `CharType` en una representación interna de una secuencia de valores.

```cpp
result in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parámetros

*Estado*\
El estado de conversión que se mantiene entre las llamadas a la función miembro.

*first1*\
Puntero al principio de la secuencia que se va a convertir.

*last1*\
Puntero al final de la secuencia que se va a convertir.

*next1*\
Puntero más allá del final de la secuencia convertida, al primer carácter sin convertir.

*first2*\
Puntero al principio de la secuencia convertida.

*last2*\
Puntero al final de la secuencia convertida.

*next2*\
Puntero a `CharType` la que viene `Chartype` después del último convertido en el primer carácter inalterado en la secuencia de destino.

### <a name="return-value"></a>Valor devuelto

Un valor devuelto que indica si la operación se ha realizado correctamente, parcialmente o no se ha realizado correctamente. La función devuelve:

- `codecvt_base::error`si la secuencia de origen está mal formada.

- `codecvt_base::noconv` si la función no realiza ninguna conversión.

- `codecvt_base::ok`si la conversión tiene éxito.

- `codecvt_base::partial`si el origen es insuficiente o si el destino no es lo suficientemente grande como para que la conversión se realice correctamente.

### <a name="remarks"></a>Observaciones

*estado* debe representar el estado de conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. Después de una conversión parcial, el *estado* debe establecerse para permitir que la conversión se reanude cuando lleguen nuevos caracteres.

La función miembro devuelve [do_in](#do_in)`( state, first1,  last1,  next1, first2, last2,  next2)`.

### <a name="example"></a>Ejemplo

```cpp
// codecvt_in.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));
   const char* pszNext;
   wchar_t* pwszNext;
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).in( state,
          pszExt, &pszExt[strlen(pszExt)], pszNext,
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;
   exit(-1);
}
```

```Output
It worked! The converted string is:
[This is the string to be converted!]
```

## <a name="codecvtintern_type"></a><a name="intern_type"></a>codecvt::intern_type

Tipo de carácter que se usa para las representaciones internas.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `CharType`.

## <a name="codecvtlength"></a><a name="length"></a>codecvt::length

Determina cuántos `Byte` valores de una `Byte` secuencia determinada de valores externos `CharType` producen no más `Byte` de un número determinado de valores internos y devuelve ese número de valores.

```cpp
int length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parámetros

*Estado*\
El estado de conversión que se mantiene entre las llamadas a la función miembro.

*first1*\
Puntero al principio de la secuencia externa.

*last1*\
Puntero al final de la secuencia externa.

*len2*\
El número máximo de Bytes que puede devolver la función miembro.

### <a name="return-value"></a>Valor devuelto

Entero que representa un recuento del número máximo de conversiones, no mayor que *len2*, definido por la secuencia de origen externa en [ `first1`, `last1`).

### <a name="remarks"></a>Observaciones

La función miembro devuelve [do_length](#do_length)`( state, first1, last1, len2)`.

### <a name="example"></a>Ejemplo

```cpp
// codecvt_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string whose length is to be measured!";
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).length( state,
          pszExt, &pszExt[strlen(pszExt)], LEN );
   cout << "The length of the string is: ";
   wcout << res;
   cout << "." << endl;
   exit(-1);
}
```

```Output
The length of the string is: 50.
```

## <a name="codecvtmax_length"></a><a name="max_length"></a>codecvt::max_length

Devuelve el número `Byte` máximo de valores `CharType`externos necesarios para producir un archivo .

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Valor devuelto

El número `Byte` máximo de valores `CharType`necesarios para producir uno .

### <a name="remarks"></a>Observaciones

La función miembro devuelve [do_max_length](#do_max_length).

### <a name="example"></a>Ejemplo

```cpp
// codecvt_max_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc( "C");//English_Britain" );//German_Germany
   int res = use_facet<codecvt<char, char, mbstate_t> >
     ( loc ).max_length( );
   wcout << res << endl;
}
```

```Output
1
```

## <a name="codecvtout"></a><a name="out"></a>codecvt::out

Convierte una secuencia `CharType` de valores internos `Byte` en una secuencia de valores externos.

```cpp
result out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parámetros

*Estado*\
El estado de conversión que se mantiene entre las llamadas a la función miembro.

*first1*\
Puntero al principio de la secuencia que se va a convertir.

*last1*\
Puntero al final de la secuencia que se va a convertir.

*next1*\
Referencia a un puntero al `CharType` primer `CharType` no convertido después de la última conversión.

*first2*\
Puntero al principio de la secuencia convertida.

*last2*\
Puntero al final de la secuencia convertida.

*next2*\
Haga referencia a un puntero `Byte` al primer `Byte`no convertido después de la última conversión .

### <a name="return-value"></a>Valor devuelto

La función miembro devuelve [do_out](#do_out)`( state, first1, last1, next1, first2, last2, next2)`.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [codecvt::do_out](#do_out).

### <a name="example"></a>Ejemplo

```cpp
// codecvt_out.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
#include <wchar.h>
using namespace std;
#define LEN 90
int main( )
{
   char pszExt[LEN+1];
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );
   char* pszNext;
   const wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).out( state,
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );
   pszExt[wcslen( pwszInt )] = 0;
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )
   << "The converted string is:\n ["
   << &pszExt[0]
   << "]" << endl;
}
```

```Output
It worked: The converted string is:
[This is the wchar_t string to be converted.]
```

## <a name="codecvtstate_type"></a><a name="state_type"></a>codecvt::state_type

Tipo de carácter que se usa para representar los estados intermedios durante las conversiones entre las representaciones internas y externas.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `StateType`.

## <a name="codecvtunshift"></a><a name="unshift"></a>codecvt::unshift

Proporciona `Byte` los valores necesarios en una conversión dependiente del `Byte` estado para completar el último carácter de una secuencia de valores.

```cpp
result unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parámetros

*Estado*\
El estado de conversión que se mantiene entre las llamadas a la función miembro.

*first2*\
Puntero a la primera posición del intervalo de destino.

*last2*\
Puntero a la última posición del intervalo de destino.

*next2*\
Puntero al primer elemento sin modificaciones en la secuencia de destino.

### <a name="return-value"></a>Valor devuelto

La función devuelve:

- `codecvt_base::error`si el estado representa un estado no válido.

- `codecvt_base::noconv` si la función no realiza ninguna conversión.

- `codecvt_base::ok`si la conversión tiene éxito.

- `codecvt_base::partial`si el destino no es lo suficientemente grande como para que la conversión tenga éxito.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida `CharType`intenta convertir el elemento de origen `first2`(0) en una secuencia de destino que almacena dentro de [ , `last2`), excepto para el elemento `Byte`de terminación (0). Siempre almacena en *next2* un puntero al primer elemento inalterado de la secuencia de destino.

*estado* debe representar el estado de conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. Normalmente, la conversión `CharType`del elemento de origen (0) deja el estado actual en el estado de conversión inicial.

La función miembro devuelve [do_unshift](#do_unshift)`( state, first2, last2, next2 )`.

## <a name="see-also"></a>Consulte también

[\<>de la localidad](../standard-library/locale.md)\
[Páginas de códigos](../c-runtime-library/code-pages.md)\
[Nombres de configuración regional, idiomas y cadenas de país/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
