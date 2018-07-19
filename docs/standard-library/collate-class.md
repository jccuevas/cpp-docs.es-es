---
title: collate (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 604d8a2082d609e85e4c55f1d4ae3b6d15c4ce22
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966464"
---
# <a name="collate-class"></a>collate (Clase)

Una clase de plantilla que describe un objeto que puede actuar como faceta de configuración regional para controlar la ordenación y agrupación de los caracteres de una cadena, las comparaciones entre ellos y el hash de las cadenas.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parámetros

*CharType* tipo usado dentro de un programa para codificar los caracteres.

## <a name="remarks"></a>Comentarios

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en `id`. En algunos lenguajes, los caracteres se agrupan y se tratan como un carácter individual y, en otros, los caracteres individuales se tratan como si fueran dos caracteres. Los servicios de intercalación que proporciona la clase collate ofrecen una manera de ordenar estos casos.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[collate](#collate)|El constructor para los objetos de la clase `collate` que actúa como una faceta de configuración regional para controlar las convenciones de ordenación de cadenas.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[char_type](#char_type)|Un tipo que describe un carácter de tipo `CharType`.|
|[string_type](#string_type)|Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo `CharType`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[compare](#compare)|Compara la igualdad o la desigualdad de dos secuencias de caracteres según las reglas específicas de su faceta.|
|[do_compare](#do_compare)|Función virtual a la que se llama para comparar la igualdad o la desigualdad de dos secuencias de caracteres según las reglas específicas de su faceta.|
|[do_hash](#do_hash)|Función virtual a la que se llama para determinar el valor hash de las secuencias según las reglas específicas de su faceta.|
|[do_transform](#do_transform)|Función virtual a la que se llama para convertir una secuencia de caracteres de una configuración regional en una cadena que se puede usar en comparaciones lexicográficas con otras secuencias de caracteres convertidas de igual forma a partir de la misma configuración regional.|
|[hash](#hash)|Determina el valor hash de la secuencia según las reglas específicas de su faceta.|
|[transform](#transform)|Convierte una secuencia de caracteres de una configuración regional en una cadena que se puede usar en comparaciones lexicográficas con otras secuencias de caracteres convertidas de forma similar a partir de la misma configuración regional.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="char_type"></a>  collate::char_type

Un tipo que describe un carácter de tipo `CharType`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `CharType`.

## <a name="collate"></a>  collate::collate

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

*_Refs* valor entero utilizado para especificar el tipo de administración de memoria para el objeto.

*_Locname* el nombre de la configuración regional.

### <a name="remarks"></a>Comentarios

Los valores posibles de la *_Refs* parámetro y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \> 1: no se definen estos valores.

El constructor inicializa su objeto base con **locale::**[faceta](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="compare"></a>  collate::compare

Compara la igualdad o la desigualdad de dos secuencias de caracteres según las reglas específicas de su faceta.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parámetros

*first1* puntero al primer elemento en la primera secuencia que se va a comparar.

*last1* puntero al último elemento en la primera secuencia que se va a comparar.

*first2* puntero al primer elemento en la segunda secuencia que se va a comparar.

*last2* puntero al último elemento en la segunda secuencia que se va a comparar.

### <a name="return-value"></a>Valor devuelto

La función miembro devuelve:

- -1 si la primera secuencia compara menos que la segunda secuencia.

- +1 si la segunda secuencia compara menos que la primera secuencia.

- 0 si las secuencias son equivalentes.

### <a name="remarks"></a>Comentarios

La primera secuencia compara menos si tiene el menor elemento del par desigual más antiguo en las secuencias o si no existe ningún par desigual, pero la primera secuencia es más corta.

La función miembro devuelve [do_compare](#do_compare)( `first1`, `last1`, `first2`, `last2`).

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

## <a name="do_compare"></a>  collate::do_compare

Función virtual a la que se llama para comparar la igualdad o la desigualdad de dos secuencias de caracteres según las reglas específicas de su faceta.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parámetros

*first1* puntero al primer elemento en la primera secuencia que se va a comparar.

*last1* puntero al último elemento en la primera secuencia que se va a comparar.

*first2* puntero al primer elemento en la segunda secuencia que se va a comparar.

*last2* puntero al último elemento en la segunda secuencia que se va a comparar.

### <a name="return-value"></a>Valor devuelto

La función miembro devuelve:

- -1 si la primera secuencia compara menos que la segunda secuencia.

- +1 si la segunda secuencia compara menos que la primera secuencia.

- 0 si las secuencias son equivalentes.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida compara la secuencia en [* first1, Last1) * con la secuencia en *[first2, last2*). Compara valores aplicando `operator<` entre los pares de elementos correspondientes de tipo `CharType`. La primera secuencia compara menos si tiene el menor elemento del par desigual más antiguo en las secuencias o, si no existe ningún par desigual, pero la primera secuencia es más corta.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [collate::compare](#compare), que llama a `do_compare`.

## <a name="do_hash"></a>  collate::do_hash

Función virtual a la que se llama para determinar el valor hash de las secuencias según las reglas específicas de su faceta.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*primera* es un puntero al primer carácter en la secuencia cuyo valor hash tiene que determinarse.

*último* es un puntero al último carácter en la secuencia cuyo valor hash tiene que determinarse.

### <a name="return-value"></a>Valor devuelto

Un valor hash de tipo **long** para la secuencia.

### <a name="remarks"></a>Comentarios

Un valor hash puede ser útil, por ejemplo, para distribuir secuencias de forma pseudoaleatoria entre una matriz de listas.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [hash](#hash), que llama a `do_hash`.

## <a name="do_transform"></a>  collate::do_transform

Función virtual a la que se llama para convertir una secuencia de caracteres de una configuración regional en una cadena que se puede usar en comparaciones lexicográficas con otras secuencias de caracteres convertidas de igual forma a partir de la misma configuración regional.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*primera* un puntero al primer carácter de la secuencia que se va a convertir.

*último* un puntero al último carácter en la secuencia que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Una cadena que es la secuencia de caracteres transformada.

### <a name="remarks"></a>Comentarios

La función de miembro virtual protegida devuelve un objeto de clase [string_type](#string_type) cuya secuencia controlada es una copia de la secuencia [ `first`, `last`). Si una clase derivada de collate\< **CharType**> reemplaza a [do_compare](#do_compare), también debe reemplazar a `do_transform` para que coincida. Cuando se pasan a `collate::compare`, dos cadenas transformadas deben producir el mismo resultado que se obtendría al pasar las cadenas sin transformar para comparar en la clase derivada.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [transform](#transform), que llama a `do_transform`.

## <a name="hash"></a>  collate::hash

Determina el valor hash de la secuencia según las reglas específicas de su faceta.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*primera* es un puntero al primer carácter en la secuencia cuyo valor hash tiene que determinarse.

*último* es un puntero al último carácter en la secuencia cuyo valor hash tiene que determinarse.

### <a name="return-value"></a>Valor devuelto

Un valor hash de tipo **long** para la secuencia.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_hash](#do_hash)( `first`, `last`).

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

## <a name="string_type"></a>  collate::string_type

Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo `CharType`.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [basic_string](../standard-library/basic-string-class.md) cuyos objetos pueden almacenar copias de la secuencia de origen.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo declarar y usar `string_type`, vea [transform](#transform).

## <a name="transform"></a>  collate::transform

Convierte una secuencia de caracteres de una configuración regional en una cadena que se puede usar en comparaciones lexicográficas con otras secuencias de caracteres convertidas de forma similar a partir de la misma configuración regional.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*primera* un puntero al primer carácter de la secuencia que se va a convertir.

*último* un puntero al último carácter en la secuencia que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Una cadena que contiene la secuencia de caracteres transformada.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_transform](#do_transform)(`first`, `last`).

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

## <a name="see-also"></a>Vea también

[\<locale>](../standard-library/locale.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
