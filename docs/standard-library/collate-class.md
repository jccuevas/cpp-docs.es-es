---
title: collate (Clase)
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate
- locale/std::collate::char_type
- locale/std::collate::string_type
- locale/std::collate::compare
- locale/std::collate::do_compare
- locale/std::collate::do_hash
- locale/std::collate::do_transform
- locale/std::collate::hash
- locale/std::collate::transform
helpviewer_keywords:
- std::collate [C++]
- std::collate [C++], char_type
- std::collate [C++], string_type
- std::collate [C++], compare
- std::collate [C++], do_compare
- std::collate [C++], do_hash
- std::collate [C++], do_transform
- std::collate [C++], hash
- std::collate [C++], transform
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
ms.openlocfilehash: f05c2e9482f8a0bada3868fdc946d4d26a0e0e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371931"
---
# <a name="collate-class"></a>collate (Clase)

Plantilla de clase que describe un objeto que puede servir como una faceta de configuración regional para controlar el orden y la agrupación de caracteres dentro de una cadena, comparaciones entre ellos y el hash de cadenas.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parámetros

*CharType*\
Tipo usado dentro de un programa para codificar caracteres.

## <a name="remarks"></a>Observaciones

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en `id`. En algunos lenguajes, los caracteres se agrupan y se tratan como un carácter individual y, en otros, los caracteres individuales se tratan como si fueran dos caracteres. Los servicios de intercalación que proporciona la clase collate ofrecen una manera de ordenar estos casos.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[Collate](#collate)|El constructor para los objetos de la clase `collate` que actúa como una faceta de configuración regional para controlar las convenciones de ordenación de cadenas.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Un tipo que describe un carácter de tipo `CharType`.|
|[string_type](#string_type)|Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo `CharType`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Comparar](#compare)|Compara la igualdad o la desigualdad de dos secuencias de caracteres según las reglas específicas de su faceta.|
|[do_compare](#do_compare)|Función virtual a la que se llama para comparar la igualdad o la desigualdad de dos secuencias de caracteres según las reglas específicas de su faceta.|
|[do_hash](#do_hash)|Función virtual a la que se llama para determinar el valor hash de las secuencias según las reglas específicas de su faceta.|
|[do_transform](#do_transform)|Función virtual a la que se llama para convertir una secuencia de caracteres de una configuración regional en una cadena que se puede usar en comparaciones lexicográficas con otras secuencias de caracteres convertidas de igual forma a partir de la misma configuración regional.|
|[Hash](#hash)|Determina el valor hash de la secuencia según las reglas específicas de su faceta.|
|[Transformar](#transform)|Convierte una secuencia de caracteres de una configuración regional en una cadena que se puede usar en comparaciones lexicográficas con otras secuencias de caracteres convertidas de forma similar a partir de la misma configuración regional.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="collatechar_type"></a><a name="char_type"></a>collate::char_type

Un tipo que describe un carácter de tipo `CharType`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `CharType`.

## <a name="collatecollate"></a><a name="collate"></a>collate::collate

El constructor para los objetos de la clase collate que actúa como una faceta de configuración regional para controlar las convenciones de ordenación de cadenas.

```cpp
public:
    explicit collate(
    size_t _Refs = 0);

protected:
    collate(
const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

*_Refs*\
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

*_Locname*\
El nombre de la configuración regional.

### <a name="remarks"></a>Observaciones

Los valores posibles para el parámetro *_Refs* y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \>1: Estos valores no están definidos.

El constructor inicializa su objeto base con`_Refs` **locale::**[faceta](../standard-library/locale-class.md#facet_class)( ).

## <a name="collatecompare"></a><a name="compare"></a>collate::compare

Compara la igualdad o la desigualdad de dos secuencias de caracteres según las reglas específicas de su faceta.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parámetros

*first1*\
Puntero al primer elemento en la primera secuencia que se va a comparar.

*last1*\
Puntero al último elemento en la primera secuencia que se va a comparar.

*first2*\
Puntero al primer elemento en la segunda secuencia que se va a comparar.

*last2*\
Puntero al último elemento en la segunda secuencia que se va a comparar.

### <a name="return-value"></a>Valor devuelto

La función miembro devuelve:

- -1 si la primera secuencia compara menos que la segunda secuencia.

- +1 si la segunda secuencia compara menos que la primera secuencia.

- 0 si las secuencias son equivalentes.

### <a name="remarks"></a>Observaciones

La primera secuencia compara menos si tiene el menor elemento del par desigual más antiguo en las secuencias o si no existe ningún par desigual, pero la primera secuencia es más corta.

La función miembro `last1`devuelve `first2` `last2` [do_compare](#do_compare)( `first1`, , , ).

### <a name="example"></a>Ejemplo

```cpp
// collate_compare.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare ( s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result2 << endl;
}
```

## <a name="collatedo_compare"></a><a name="do_compare"></a>collate::do_compare

Función virtual a la que se llama para comparar la igualdad o la desigualdad de dos secuencias de caracteres según las reglas específicas de su faceta.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parámetros

*first1*\
Puntero al primer elemento en la primera secuencia que se va a comparar.

*last1*\
Puntero al último elemento en la primera secuencia que se va a comparar.

*first2*\
Puntero al primer elemento en la segunda secuencia que se va a comparar.

*last2*\
Puntero al último elemento en la segunda secuencia que se va a comparar.

### <a name="return-value"></a>Valor devuelto

La función miembro devuelve:

- -1 si la primera secuencia compara menos que la segunda secuencia.

- +1 si la segunda secuencia compara menos que la primera secuencia.

- 0 si las secuencias son equivalentes.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida compara la secuencia en [ * first1, Last1)* con la secuencia en *[ first2, last2*). Compara los valores aplicando `operator<` entre pares de `CharType`elementos correspondientes de tipo . La primera secuencia compara menos si tiene el menor elemento del par desigual más antiguo en las secuencias o, si no existe ningún par desigual, pero la primera secuencia es más corta.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [collate::compare](#compare), que llama a `do_compare`.

## <a name="collatedo_hash"></a><a name="do_hash"></a>collate::do_hash

Función virtual a la que se llama para determinar el valor hash de las secuencias según las reglas específicas de su faceta.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Un puntero al primer carácter de la secuencia cuyo valor hash tiene que determinarse.

*Última*\
Un puntero al último carácter de la secuencia cuyo valor hash tiene que determinarse.

### <a name="return-value"></a>Valor devuelto

Un valor hash de tipo **long** para la secuencia.

### <a name="remarks"></a>Observaciones

Un valor hash puede ser útil, por ejemplo, para distribuir secuencias de forma pseudoaleatoria entre una matriz de listas.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [hash](#hash), que llama a `do_hash`.

## <a name="collatedo_transform"></a><a name="do_transform"></a>collate::do_transform

Función virtual a la que se llama para convertir una secuencia de caracteres de una configuración regional en una cadena que se puede usar en comparaciones lexicográficas con otras secuencias de caracteres convertidas de igual forma a partir de la misma configuración regional.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Un puntero al primer carácter de la secuencia que se va a convertir.

*Última*\
Un puntero al último carácter de la secuencia que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Una cadena que es la secuencia de caracteres transformada.

### <a name="remarks"></a>Observaciones

La función miembro virtual protegida [string_type](#string_type) devuelve un objeto de clase string_type `first` `last`cuya secuencia controlada es una copia de la secuencia [ , ). Si una clase derivada de collate\< **CharType**> reemplaza a [do_compare](#do_compare), también debe reemplazar a `do_transform` para que coincida. Cuando se pasan a `collate::compare`, dos cadenas transformadas deben producir el mismo resultado que se obtendría al pasar las cadenas sin transformar para comparar en la clase derivada.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [transform](#transform), que llama a `do_transform`.

## <a name="collatehash"></a><a name="hash"></a>collate::hash

Determina el valor hash de la secuencia según las reglas específicas de su faceta.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Un puntero al primer carácter de la secuencia cuyo valor hash tiene que determinarse.

*Última*\
Un puntero al último carácter de la secuencia cuyo valor hash tiene que determinarse.

### <a name="return-value"></a>Valor devuelto

Un valor hash de tipo **long** para la secuencia.

### <a name="remarks"></a>Observaciones

La función miembro `first` `last`devuelve [do_hash](#do_hash)( , ).

Un valor hash puede ser útil, por ejemplo, para distribuir secuencias de forma pseudoaleatoria entre una matriz de listas.

### <a name="example"></a>Ejemplo

```cpp
// collate_hash.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("\x00dfzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet
   _TCHAR * s2 = _T("zzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet

   long r1 = use_facet< collate<_TCHAR> > ( loc ).
      hash (s1, &s1[_tcslen( s1 )-1 ]);
   long r2 =  use_facet< collate<_TCHAR> > ( loc ).
      hash (s2, &s2[_tcslen( s2 )-1 ] );
   cout << r1 << " " << r2 << endl;
}
```

```Output
541187293 551279837
```

## <a name="collatestring_type"></a><a name="string_type"></a>collate::string_type

Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo `CharType`.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de plantilla de clase [basic_string](../standard-library/basic-string-class.md) cuyos objetos pueden almacenar copias de la secuencia de origen.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo declarar y usar `string_type`, vea [transform](#transform).

## <a name="collatetransform"></a><a name="transform"></a>collate::transform

Convierte una secuencia de caracteres de una configuración regional en una cadena que se puede usar en comparaciones lexicográficas con otras secuencias de caracteres convertidas de forma similar a partir de la misma configuración regional.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Un puntero al primer carácter de la secuencia que se va a convertir.

*Última*\
Un puntero al último carácter de la secuencia que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Una cadena que contiene la secuencia de caracteres transformada.

### <a name="remarks"></a>Observaciones

La función miembro`first` `last`devuelve [do_transform](#do_transform)( , ).

### <a name="example"></a>Ejemplo

```cpp
// collate_transform.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   _TCHAR* s1 = _T("\x00dfzz abc.");
   // \x00df is the German sharp-s (looks like beta),
   // it comes before z in the alphabet
   _TCHAR* s2 = _T("zzz abc.");

   collate<_TCHAR>::string_type r1;   // OK for typedef
   r1 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s1, &s1[_tcslen( s1 )-1 ]);

   cout << r1 << endl;

   basic_string<_TCHAR> r2 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s2, &s2[_tcslen( s2 )-1 ]);

   cout << r2 << endl;

   int result1 = use_facet<collate<_TCHAR> > ( loc ).compare
      (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );

   cout << _tcscmp(r1.c_str( ),r2.c_str( )) << result1
      << _tcscmp(s1,s2) <<endl;
}
```

```Output

-1-11
```

## <a name="see-also"></a>Consulte también

[\<>de la localidad](../standard-library/locale.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
