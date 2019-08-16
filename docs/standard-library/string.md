---
title: '&lt;string&gt;'
ms.date: 11/04/2016
f1_keywords:
- string/std::<string>
- <string>
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 80d5d297cc28cfb019dae99e9e9736e4b2eb654f
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957132"
---
# <a name="ltstringgt"></a>&lt;string&gt;

Define la clase de plantilla de contenedores `basic_string` y diversas plantillas auxiliares.

Para más información sobre `basic_string`, vea [basic_string (Clase)](../standard-library/basic-string-class.md)

## <a name="syntax"></a>Sintaxis

```cpp
#include <string>
```

## <a name="remarks"></a>Comentarios

El lenguaje C++ y la biblioteca estándar de C++ admiten dos tipos de cadenas:

- Matrices de caracteres terminadas en null, que a menudo se llaman “cadenas de C”.

- Objetos de clase de plantilla, `basic_string`de tipo, que administran todos los argumentos de plantilla similares a **Char**.

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|DESCRIPCIÓN|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|Tipo que describe una especialización de la clase `basic_string` de plantilla con elementos de tipo `string`char como.|
|[wstring](../standard-library/string-typedefs.md#wstring)|Tipo que describe una especialización de la clase `basic_string` de plantilla con elementos de tipo `wstring`wchar_t como.|
|[u16string](../standard-library/string-typedefs.md#u16string)|Tipo que describe una especialización de la clase de plantilla `basic_string` basada en elementos de tipo `char16_t`.|
|[u32string](../standard-library/string-typedefs.md#u32string)|Tipo que describe una especialización de la clase de plantilla `basic_string` basada en elementos de tipo `char32_t`.|

### <a name="operators"></a>Operadores

|Operador|DESCRIPCIÓN|
|-|-|
|[operator+](../standard-library/string-operators.md#op_add)|Concatena dos objetos de cadena.|
|[operator!=](../standard-library/string-operators.md#op_neq)|Comprueba si el objeto de cadena del lado izquierdo del operador no es igual que el objeto de cadena del lado derecho.|
|[operator==](../standard-library/string-operators.md#op_eq_eq)|Comprueba si el objeto de cadena del lado izquierdo del operador es igual que el objeto de cadena del lado derecho.|
|[operator<](../standard-library/string-operators.md#op_lt)|Comprueba si el objeto de cadena del lado izquierdo del operador es menor que el objeto de cadena del lado derecho.|
|[operator<=](../standard-library/string-operators.md#op_lt_eq)|Comprueba si el objeto de cadena del lado izquierdo del operador es menor o igual que el objeto de cadena del lado derecho.|
|[operator<\<](../standard-library/string-operators.md#op_lt_lt)|Función de plantilla que inserta una cadena en la secuencia de salida.|
|[operator>](../standard-library/string-operators.md#op_gt)|Comprueba si el objeto de cadena del lado izquierdo del operador es mayor que el objeto de cadena del lado derecho.|
|[operator>=](../standard-library/string-operators.md#op_gt_eq)|Comprueba si el objeto de cadena del lado izquierdo del operador es mayor o igual que el objeto de cadena del lado derecho.|
|[operator>>](../standard-library/string-operators.md#op_gt_gt)|Función de plantilla que extrae una cadena de la secuencia de entrada.|

### <a name="specialized-template-functions"></a>Funciones de plantilla especializadas

|||
|-|-|
|hash|Genera un hash de una cadena.|
|[swap](../standard-library/string-functions.md#swap)|Intercambia las matrices de caracteres de dos cadenas.|
|[stod](../standard-library/string-functions.md#stod)|Convierte una secuencia de caracteres en un **valor Double**.|
|[stof](../standard-library/string-functions.md#stof)|Convierte una secuencia de caracteres en un valor de **tipo float**.|
|[stoi](../standard-library/string-functions.md#stoi)|Convierte una secuencia de caracteres en un entero.|
|[stold](../standard-library/string-functions.md#stold)|Convierte una secuencia de caracteres en un **valor doble largo**.|
|[stoll](../standard-library/string-functions.md#stoll)|Convierte una secuencia de caracteres en Long **Long**.|
|[stoul](../standard-library/string-functions.md#stoul)|Convierte una secuencia de caracteres en un entero **largo sin signo**.|
|[stoull](../standard-library/string-functions.md#stoull)|Convierte una secuencia de caracteres en un entero largo **sin signo**.|
|[to_string](../standard-library/string-functions.md#to_string)|Convierte un valor en `string`.|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Convierte un valor en una `string` ancha.|

### <a name="functions"></a>Funciones

|Función|DESCRIPCIÓN|
|-|-|
|[Plantilla getline](../standard-library/string-functions.md#getline)|Extraiga las cadenas de la secuencia de entrada línea por línea.|

### <a name="classes"></a>Clases

|Clase|DESCRIPCIÓN|
|-|-|
|[basic_string (Clase)](../standard-library/basic-string-class.md)|Clase de plantilla que describe los objetos que pueden almacenar una secuencia de objetos arbitrarios similares a caracteres.|
|[char_traits (Struct)](../standard-library/char-traits-struct.md)|Clase de plantilla que describe los atributos asociados a un carácter de tipo CharType|

### <a name="specializations"></a>Especializaciones

|||
|-|-|
|[char_traits\<char> (Struct)](../standard-library/char-traits-char-struct.md)|Un struct que es una especialización del struct de plantilla `char_traits`\<CharType> para un elemento de tipo `char`.|
|[char_traits<wchar_t> (Struct)](../standard-library/char-traits-wchar-t-struct.md)|Un struct que es una especialización del struct de plantilla `char_traits`\<CharType> para un elemento de tipo `wchar_t`.|
|[char_traits<char16_t> (Struct)](../standard-library/char-traits-char16-t-struct.md)|Un struct que es una especialización del struct de plantilla `char_traits`\<CharType> para un elemento de tipo `char16_t`.|
|[char_traits<char32_t> (Struct)](../standard-library/char-traits-char32-t-struct.md)|Un struct que es una especialización del struct de plantilla `char_traits`\<CharType> para un elemento de tipo `char32_t`.|

## <a name="requirements"></a>Requisitos

- **Encabezado:** \<string>

- **Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
