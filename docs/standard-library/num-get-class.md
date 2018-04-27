---
title: num_get (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
dev_langs:
- C++
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 555c00be3e50444bd3537ad8282d5b862cb3e7ec
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="numget-class"></a>num_get (clase)

Una clase de plantilla que describe un objeto que puede actuar como una faceta de la configuración regional para controlar las conversiones de las secuencias de tipo `CharType` en valores numéricos.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Parámetros

`CharType` El tipo usado dentro de un programa para codificar los caracteres de una configuración regional.

`InputIterator` El tipo de iterador del que las funciones get numéricas lee su entrada.

## <a name="remarks"></a>Comentarios

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[num_get](#num_get)|Constructor para los objetos de tipo `num_get` que se usan para extraer valores numéricos de secuencias.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|
|[iter_type](#iter_type)|Tipo que describe un iterador de entrada.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[do_get](#do_get)|Función virtual a la que se llama para extraer un valor numérico o un valor booleano de una secuencia de caracteres.|
|[get](#get)|Extrae un valor numérico o un valor booleano de una secuencia de caracteres.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="char_type"></a> num_get::char_type

Tipo que se usa para describir un carácter empleado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla **CharType**.

## <a name="do_get"></a> num_get::do_get

Función virtual a la que se llama para extraer un valor numérico o un valor booleano de una secuencia de caracteres.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

### <a name="parameters"></a>Parámetros

`first` El comienzo del intervalo de caracteres desde la que se va a leer el número.

`last` El final del intervalo de caracteres desde la que se va a leer el número.

`_Iosbase` El [ios_base](../standard-library/ios-base-class.md) cuyos indicadores se utilizan por la conversión.

`_State` El estado de a qué failbit (vea [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)) se agrega en caso de error.

`val` El valor que se ha leído.

### <a name="return-value"></a>Valor devuelto

El iterador después de que el valor se haya leído.

### <a name="remarks"></a>Comentarios

La primera función miembro virtual protegida,

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
```

coincide con elementos secuenciales, empezando por `first` en la secuencia `[first, last)` hasta que se reconoce una completa, el campo de entrada de enteros no vacío. Si tiene éxito, convierte este campo a su valor equivalente como tipo `long`y almacena el resultado en `val`. Devuelve un iterador que designa el primer elemento más allá del campo de entrada numérico. De otro modo, la función no almacena nada en `val` y establece `ios_base::failbit` en `state`. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de un campo de entrada numérico entero válido. En cualquier caso, si el valor devuelto es igual a `last`, la función establece `ios_base::eofbit` en `state`.

El campo de entrada numérico entero se convierte mediante las mismas reglas que han usado las funciones de análisis para hacer coincidir y convertir una serie de elementos `char` de un archivo. (Se presupone que cada uno de estos elementos `char` se asigna a un elemento equivalente de tipo `Elem` mediante una asignación simple, uno a uno). La especificación de conversión de análisis equivalente se determina de la manera siguiente:

Si `iosbase.`[ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), la especificación de conversión es `lo`.

Si `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), la especificación de conversión es `lx`.

Si `iosbase.flags() & ios_base::basefield == 0`, la especificación de conversión es `li`.

De otro modo, la especificación de conversión es `ld`.

El formato de un campo de entrada numérico entero se determina por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class)`fac` que se devuelve mediante la llamada a [use_facet](../standard-library/locale-functions.md#use_facet) `<`[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.` [ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. De manera específica:

`fac.` [numpunct::grouping](../standard-library/numpunct-class.md#grouping) `()` determina cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.

`fac.` [numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` determina la secuencia que separa grupos de dígitos a la izquierda de cualquier separador decimal.

Si no se produce ninguna instancia de `fac.thousands_sep()` en el campo de entrada numérico, no se impone ninguna restricción de agrupación. De otro modo, se aplica cualquier restricción de agrupación impuesta por `fac.grouping()` y los separadores se quitan antes de que se produzca la conversión de análisis.

La cuarta función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

se comporta igual que la primera, excepto que reemplaza una especificación de conversión de `ld` por `lu`. Si se realiza correctamente, convierte el campo de entrada numérico en un valor de tipo `unsigned long` y almacena ese valor en `val`.

La quinta función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;
```

se comporta igual que la primera, excepto que reemplaza una especificación de conversión de `ld` por `lld`. Si se realiza correctamente, convierte el campo de entrada numérico en un valor de tipo `long long` y almacena ese valor en `val`.

La sexta función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;
```

se comporta igual que la primera, excepto que reemplaza una especificación de conversión de `ld` por `llu`. Si se realiza correctamente, convierte el campo de entrada numérico en un valor de tipo `unsigned long long` y almacena ese valor en `val`.

La séptima función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;
```

se comporta igual que la primera, excepto que intenta coincidir con un campo de entrada de punto flotante completo y que no esté vacío. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` determina la secuencia que separa los dígitos enteros de los dígitos de fracción. El especificador de conversión de análisis equivalente es `lf`.

La octava función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

se comporta igual que la primera, excepto que intenta coincidir con un campo de entrada de punto flotante completo y que no esté vacío. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` determina la secuencia que separa los dígitos enteros de los dígitos de fracción. El especificador de conversión de análisis equivalente es `lf`.

La novena función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

se comporta igual que la octava, excepto que el especificador de conversión de análisis equivalente es `Lf`.

La función miembro protegido virtual décima:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

se comporta igual que la primera, excepto que el especificador de conversión de análisis equivalente es `p`.

La última (undécima) función miembro virtual protegida:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

se comporta igual que la primera, excepto que intenta coincidir con un campo de entrada booleano completo y que no esté vacío. Si se realiza correctamente, convierte el campo de entrada booleano en un valor de tipo `bool` y almacena ese valor en `val`.

Un campo de entrada booleano adopta una de dos formas. Si `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) es False, es igual que un campo de entrada numérico entero, excepto que el valor convertido debe ser 0 (para False) o 1 (para True). De otro modo, la secuencia debe coincidir con `fac.`[numpunct::falsename](../standard-library/numpunct-class.md#falsename)`()` (para False), o con `fac.`[numpunct::truename](../standard-library/numpunct-class.md#truename)`()` (para True).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get](#get), donde `do_get` llama a la función miembro virtual.

## <a name="get"></a> num_get::get

Extrae un valor numérico o un valor booleano de una secuencia de caracteres.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

### <a name="parameters"></a>Parámetros

`first` El comienzo del intervalo de caracteres desde la que se va a leer el número.

`last` El final del intervalo de caracteres desde la que se va a leer el número.

`_Iosbase` El [ios_base](../standard-library/ios-base-class.md) cuyos indicadores se utilizan por la conversión.

`_State` El estado de a qué failbit (vea [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)) se agrega en caso de error.

`val` El valor que se ha leído.

### <a name="return-value"></a>Valor devuelto

El iterador después de que el valor se haya leído.

### <a name="remarks"></a>Comentarios

Todas las funciones miembro devuelven [do_get](#do_get)( `first` `last` `_Iosbase`, `_State`, `val`).

La primera función miembro virtual protegida intenta comparar los elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que reconoce un campo de entrada numérico entero completo y que no esté vacío. Si se realiza correctamente, convierte este campo en su valor equivalente como el tipo **long** y almacena el resultado en `val`. Devuelve un iterador que designa el primer elemento más allá del campo de entrada numérico. De otro modo, la función no almacena nada en `val` y establece `ios_base::failbit` en _ *State*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de un campo de entrada numérico entero válido. En cualquier caso, si el valor devuelto es igual a **last**, la función establece `ios_base::eofbit` en `_State`.

El campo de entrada numérico entero se convierte mediante las mismas reglas que han usado las funciones de análisis para hacer coincidir y convertir una serie de elementos `char` de un archivo. Se supone que cada uno de estos elementos `char` se asigna a un elemento equivalente de tipo **CharType** mediante una asignación simple, uno a uno. La especificación de conversión de análisis equivalente se determina de la manera siguiente:

- Si **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct), la especificación de conversión es **lo**.

- Si **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex), la especificación de conversión es **lx**.

- Si **iosbase.flags** & **ios_base::basefield** == 0, la especificación de conversión es `li`.

- De otro modo, la especificación de conversión es **ld**.

El formato de un campo de entrada numérico entero se determina por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class)**fac** que se devuelve mediante la llamada a [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). De manera específica:

- **fac**. [grouping](../standard-library/numpunct-class.md#grouping) determina cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) determina la secuencia que separa grupos de dígitos a la izquierda de cualquier separador decimal.

Si ninguna instancia de **fac**. `thousands_sep` se produce en el campo de entrada numérico, no se impone ninguna restricción de agrupación. De otro modo, cualquier restricción de agrupación impuesta por **fac**. **grouping** se aplica y los separadores se quitan antes de que se produzca la conversión de análisis.

La segunda función miembro virtual protegida:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

se comporta igual que la primera, excepto que reemplaza una especificación de conversión de **ld** por **lu**. Si se realiza correctamente, convierte el campo de entrada numérico en un valor de tipo `unsigned long` y almacena ese valor en `val`.

La tercera función miembro virtual protegida:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

se comporta igual que la primera, excepto que intenta coincidir con un campo de entrada de punto flotante completo y que no esté vacío. **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) determina la secuencia que separa los dígitos enteros de los dígitos de fracción. El especificador de conversión de análisis equivalente es **lf**.

La cuarta función miembro virtual protegida:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

se comporta igual que la tercera, excepto que el especificador de conversión de análisis equivalente es **Lf**.

La quinta función miembro virtual protegida:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

se comporta igual que la primera, excepto que el especificador de conversión de análisis equivalente es **p**.

La sexta función miembro virtual protegida:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

se comporta igual que la primera, excepto que intenta coincidir con un campo de entrada booleano completo y que no esté vacío. Si se realiza correctamente, convierte el campo de entrada booleano en un valor de tipo `bool` y almacena ese valor en `val`.

Un campo de entrada booleano adopta una de dos formas. Si **iosbase**. **flags** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) es **False**, es igual que un campo de entrada numérico entero, excepto que el valor convertido debe ser 0 (para **False**) o 1 (para **True**). De otro modo, la secuencia debe coincidir con **fac**. [falsename](../standard-library/numpunct-class.md#falsename) (para **False**) o con **fac**. [truename](../standard-library/numpunct-class.md#truename) (para **True**).

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

## <a name="iter_type"></a> num_get::iter_type

Tipo que describe un iterador de entrada.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla **InputIterator**.

## <a name="num_get"></a> num_get::num_get

Constructor para los objetos de tipo `num_get` que se usan para extraer valores numéricos de secuencias.

```cpp
explicit num_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

`_Refs` Valor de entero utilizado para especificar el tipo de administración de memoria para el objeto.

### <a name="remarks"></a>Comentarios

Los valores posibles del parámetro `_Refs` y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \> 1: no se definen estos valores.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa su objeto base con **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="see-also"></a>Vea también

[\<locale>](../standard-library/locale.md)<br/>
[Facet (clase)](../standard-library/locale-class.md#facet_class)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
