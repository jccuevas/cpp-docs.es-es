---
title: num_get (clase)
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
ms.openlocfilehash: 76d2832141c65ca67c42f1994a3c8f5b532f0092
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373654"
---
# <a name="num_get-class"></a>num_get (clase)

Plantilla de clase que describe un objeto que puede servir como faceta `CharType` de configuración regional para controlar las conversiones de secuencias de tipo a valores numéricos.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Parámetros

*CharType*\
Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.

*InputIterator*\
El tipo de iterador del que las funciones get numéricas leen su entrada.

## <a name="remarks"></a>Observaciones

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[num_get](#num_get)|Constructor para los objetos de tipo `num_get` que se usan para extraer valores numéricos de secuencias.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|
|[iter_type](#iter_type)|Tipo que describe un iterador de entrada.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[do_get](#do_get)|Función virtual a la que se llama para extraer un valor numérico o un valor booleano de una secuencia de caracteres.|
|[get](#get)|Extrae un valor numérico o un valor booleano de una secuencia de caracteres.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="num_getchar_type"></a><a name="char_type"></a>num_get::char_type

Tipo que se usa para describir un carácter empleado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla **CharType**.

## <a name="num_getdo_get"></a><a name="do_get"></a>num_get::do_get

Función virtual a la que se llama para extraer un valor numérico o un valor booleano de una secuencia de caracteres.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
El principio del intervalo de caracteres del que se va a leer el número.

*Última*\
El final del intervalo de caracteres del que se va a leer el número.

*iosbase*\
El objeto [ios_base](../standard-library/ios-base-class.md) cuyas marcas se usan por la conversión.

*Estado*\
El estado al que failbit (ver [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) se agrega en caso de error.

*Val*\
Valor que se leyó.

### <a name="return-value"></a>Valor devuelto

El iterador después de que el valor se haya leído.

### <a name="remarks"></a>Observaciones

La primera función miembro virtual protegida,

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;
```

coincide con los *first* elementos `[first, last)` secuenciales que comienzan al principio en la secuencia hasta que ha reconocido un campo de entrada entero completo y no vacío. Si se realiza correctamente, convierte este campo a su valor equivalente como tipo **long**y almacena el resultado en *val*. Devuelve un iterador que designa el primer elemento más allá del campo de entrada numérico. De lo contrario, la función `state`no almacena nada en *val* y establece `ios_base::failbit` en . Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de un campo de entrada numérico entero válido. En cualquier caso, si el valor devuelto es igual a `last`, la función establece `ios_base::eofbit` en `state`.

El campo de entrada entero se convierte mediante las mismas reglas utilizadas por las funciones de análisis para hacer coincidir y convertir una serie de elementos **char** de un archivo. (Se supone que cada elemento **char** se `Elem` asigna a un elemento equivalente de tipo mediante una asignación simple, uno a uno.) La especificación de conversión de escaneado equivalente se determina de la siguiente manera:

Si `iosbase.` [ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), `lo`la especificación de conversión es .

Si `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), la especificación de conversión es `lx`.

Si `iosbase.flags() & ios_base::basefield == 0`, la especificación de conversión es `li`.

De otro modo, la especificación de conversión es `ld`.

El formato de un campo de entrada entero viene determinado además por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class) `fac` devuelta por la llamada [use_facet](../standard-library/locale-functions.md#use_facet) `<` [numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. Concretamente:

`fac.`[numpunct::grouping](../standard-library/numpunct-class.md#grouping) `()` determina cómo se agrupan los dígitos a la izquierda de cualquier punto decimal

`fac.`[numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` determina la secuencia que separa los grupos de dígitos a la izquierda de cualquier punto decimal.

Si no se produce ninguna instancia de `fac.thousands_sep()` en el campo de entrada numérico, no se impone ninguna restricción de agrupación. De otro modo, se aplica cualquier restricción de agrupación impuesta por `fac.grouping()` y los separadores se quitan antes de que se produzca la conversión de análisis.

La cuarta función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

se comporta igual que la primera, excepto que reemplaza una especificación de conversión de `ld` por `lu`. Si se realiza correctamente, convierte el campo de entrada numérico en un valor de tipo **unsigned long** y almacena ese valor en *val*.

La quinta función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;
```

se comporta igual que la primera, excepto que reemplaza una especificación de conversión de `ld` por `lld`. Si se realiza correctamente, convierte el campo de entrada numérico en un valor de tipo **long long** y almacena ese valor en *val*.

La sexta función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;
```

se comporta igual que la primera, excepto que reemplaza una especificación de conversión de `ld` por `llu`. Si se realiza correctamente, convierte el campo de entrada numérico en un valor de tipo **unsigned long long** y almacena ese valor en *val*.

La séptima función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;
```

se comporta igual que la primera, excepto que intenta coincidir con un campo de entrada de punto flotante completo y que no esté vacío. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` determina la secuencia que separa los dígitos enteros de los dígitos de fracción. El especificador de conversión de análisis equivalente es `lf`.

La octava función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

se comporta igual que la primera, excepto que intenta coincidir con un campo de entrada de punto flotante completo y que no esté vacío. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` determina la secuencia que separa los dígitos enteros de los dígitos de fracción. El especificador de conversión de análisis equivalente es `lf`.

La novena función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

se comporta igual que la octava, excepto que el especificador de conversión de análisis equivalente es `Lf`.

La décima función miembro protegido virtual:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

se comporta igual que la primera, excepto que el especificador de conversión de análisis equivalente es `p`.

La última (undécima) función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

se comporta igual que la primera, excepto que intenta coincidir con un campo de entrada booleano completo y que no esté vacío. Si se realiza correctamente, convierte el campo de entrada booleano en un valor de tipo **bool** y almacena ese valor en *val*.

Un campo de entrada booleano adopta una de dos formas. Si `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) es False, es igual que un campo de entrada numérico entero, excepto que el valor convertido debe ser 0 (para False) o 1 (para True). De lo contrario, `fac.`la secuencia debe coincidir con [numpunct::falsename](../standard-library/numpunct-class.md#falsename) `()` (para false) o `fac.` [numpunct::truename](../standard-library/numpunct-class.md#truename) `()` (para true).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get](#get), donde `do_get` llama a la función miembro virtual.

## <a name="num_getget"></a><a name="get"></a>num_get::get

Extrae un valor numérico o un valor booleano de una secuencia de caracteres.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
El principio del intervalo de caracteres del que se va a leer el número.

*Última*\
El final del intervalo de caracteres del que se va a leer el número.

*iosbase*\
El objeto [ios_base](../standard-library/ios-base-class.md) cuyas marcas se usan por la conversión.

*Estado*\
El estado al que failbit (ver [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) se agrega en caso de error.

*Val*\
Valor que se leyó.

### <a name="return-value"></a>Valor devuelto

El iterador después de que el valor se haya leído.

### <a name="remarks"></a>Observaciones

Todas las funciones miembro devuelven [do_get](#do_get)`( first, last, iosbase, state, val)`.

La primera función miembro virtual protegida intenta comparar los elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que reconoce un campo de entrada numérico entero completo y que no esté vacío. Si se realiza correctamente, convierte este campo a su valor equivalente como tipo **long** y almacena el resultado en *val*. Devuelve un iterador que designa el primer elemento más allá del campo de entrada numérico. De lo contrario, la función no almacena nada en *val* y establece `ios_base::failbit` en *estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de un campo de entrada numérico entero válido. En cualquier caso, si el valor devuelto `ios_base::eofbit` es igual a *last*, la función se establece en *state*.

El campo de entrada entero se convierte mediante las mismas reglas utilizadas por las funciones de análisis para hacer coincidir y convertir una serie de elementos **char** de un archivo. Se supone que cada elemento **char** se `CharType` asigna a un elemento equivalente de tipo mediante una asignación simple de uno a uno. La especificación de conversión de análisis equivalente se determina de la manera siguiente:

- Si `iosbase.` [flags](../standard-library/ios-base-class.md#flags)`& ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), `lo`la especificación de conversión es .

- Si `iosbase.flags & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), la especificación de conversión es `lx`.

- Si `iosbase.flags & ios_base::basefield == 0`, la especificación de conversión es `li`.

- De otro modo, la especificación de conversión es `ld`.

El formato de un campo de entrada entero viene determinado además por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class) `fac` devuelta por la llamada [use_facet](../standard-library/locale-functions.md#use_facet)`<`[`numpunct`](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[getloc](../standard-library/ios-base-class.md#getloc)`())`. Concretamente:

- `fac.`[agrupación](../standard-library/numpunct-class.md#grouping) determina cómo se agrupan los dígitos a la izquierda de cualquier punto decimal.

- `fac.`[thousands_sep](../standard-library/numpunct-class.md#thousands_sep) determina la secuencia que separa los grupos de dígitos a la izquierda de cualquier punto decimal.

Si no se produce ninguna instancia de `fac.thousands_sep` en el campo de entrada numérico, no se impone ninguna restricción de agrupación. De lo contrario, se `fac.grouping` aplican las restricciones de agrupación impuestas por se aplica y los separadores se eliminan antes de que se produzca la conversión de análisis.

La segunda función miembro virtual protegida:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

se comporta igual que la primera, excepto que reemplaza una especificación de conversión de `ld` por `lu`. Si se realiza correctamente, convierte el campo de entrada numérico en un valor de tipo **unsigned long** y almacena ese valor en *val*.

La tercera función miembro virtual protegida:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

se comporta igual que la primera, excepto que intenta coincidir con un campo de entrada de punto flotante completo y que no esté vacío. `fac.`[decimal_point](../standard-library/numpunct-class.md#decimal_point) determina la secuencia que separa los dígitos enteros de los dígitos de fracción. El especificador de conversión de análisis equivalente es `lf`.

La cuarta función miembro virtual protegida:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

se comporta igual que el tercero, excepto que el `Lf`especificador de conversión de análisis equivalente es .

La quinta función miembro virtual protegida:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

se comporta igual que la primera, excepto que el especificador de conversión de análisis equivalente es `p`.

La sexta función miembro virtual protegida:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

se comporta igual que la primera, excepto que intenta coincidir con un campo de entrada booleano completo y que no esté vacío. Si se realiza correctamente, convierte el campo de entrada booleano en un valor de tipo **bool** y almacena ese valor en *val*.

Un campo de entrada booleano adopta una de dos formas. Si `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) es **false**, es lo mismo que un campo de entrada entero, excepto que el valor convertido debe ser 0 (para **false)** o 1 (para **true**). De lo contrario, `fac.`la secuencia debe coincidir `fac.`con [falsename](../standard-library/numpunct-class.md#falsename) (para **false**) o [truename](../standard-library/numpunct-class.md#truename) (para **true**).

### <a name="example"></a>Ejemplo

```cpp
// num_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   basic_stringstream<char> psz, psz2;
   psz << "-1000,56";

   ios_base::iostate st = 0;
   long double fVal;
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;

   psz.imbue( loc );
   use_facet <num_get <char> >
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter(0), psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get( ) FAILED" << endl;
   else
      cout << "money_get( ) = " << fVal << endl;
}
```

## <a name="num_getiter_type"></a><a name="iter_type"></a>num_get::iter_type

Tipo que describe un iterador de entrada.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `InputIterator`.

## <a name="num_getnum_get"></a><a name="num_get"></a>num_get::num_get

Constructor para los objetos de tipo `num_get` que se usan para extraer valores numéricos de secuencias.

```cpp
explicit num_get(size_t refs = 0);
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

El constructor inicializa su `locale::`objeto base con [faceta](../standard-library/locale-class.md#facet_class)`(refs)`.

## <a name="see-also"></a>Consulte también

[\<>de la localidad](../standard-library/locale.md)\
[faceta Clase](../standard-library/locale-class.md#facet_class)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
