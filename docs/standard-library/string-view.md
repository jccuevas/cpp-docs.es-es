---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 8952416cf37fc4d8d281d6ced9b8264495ec3799
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346983"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

Define la plantilla de clase `basic_string_view` y relacionados con los tipos y operadores. (Requiere la opción del compilador [std: c ++ 17](../build/reference/std-specify-language-standard-version.md) o una versión posterior.)

## <a name="syntax"></a>Sintaxis

```cpp
#include <string_view>
```

## <a name="remarks"></a>Comentarios

La familia de string_view de especializaciones de plantilla proporciona una manera eficaz de pasar un identificador de solo lectura, seguro para excepciones, que no es propietario a los datos de caracteres de todos los objetos de tipo cadena con el primer elemento de la secuencia en la posición cero. Un parámetro de función de tipo `string_view` (que es un typedef para `basic_string_view<char>`) puede aceptar argumentos como `std::string`, **char\***, o cualquier otra clase de tipo cadena de caracteres estrechos que implícita conversión a `string_view` está definido. De forma similar, un parámetro de `wstring_view`, `u16string_view` o `u32string_view` puede aceptar cualquier tipo de cadena para el que se define una conversión implícita. Para obtener más información, consulte [basic_string_view clase](../standard-library/basic-string-view-class.md).

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Una especialización de la plantilla de clase `basic_string_view` con elementos de tipo **char**.|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Una especialización de la plantilla de clase `basic_string_view` con elementos de tipo **wchar_t**.|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|Una especialización de la plantilla de clase `basic_string_view` con elementos de tipo `char16_t`.|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|Una especialización de la plantilla de clase `basic_string_view` con elementos de tipo `char32_t`.|

### <a name="operators"></a>Operadores

El \<string_view > pueden comparar operadores `string_view` tipos de objetos a los objetos de cualquier convertible de cadena.

|Operador|Descripción|
|-|-|
|[operator!=](../standard-library/string-view-operators.md#op_neq)|Comprueba si el objeto en el lado izquierdo del operador no es igual al objeto del lado derecho.|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|Comprueba si el objeto en el lado izquierdo del operador es igual al objeto del lado derecho.|
|[operator<](../standard-library/string-view-operators.md#op_lt)|Comprueba si el objeto en el lado izquierdo del operador es menor que el objeto en el lado derecho.|
|[operator<=](../standard-library/string-view-operators.md#op_lt_eq)|Comprueba si el objeto en el lado izquierdo del operador es menor o igual que el objeto del lado derecho.|
|[operator<\<](../standard-library/string-view-operators.md#op_lt_lt)|Una función de plantilla que inserta un `string_view` en un flujo de salida.|
|[operator>](../standard-library/string-view-operators.md#op_gt)|Comprueba si el objeto en el lado izquierdo del operador es mayor que el objeto del lado derecho.|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|Comprueba si el objeto en el lado izquierdo del operador es mayor o igual que el objeto del lado derecho.|

### <a name="literals"></a>Literales

|Operador|Descripción|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|Construye un `string_view`, `wstring_view`, `u16string_view`, o `u32string_view` según el tipo de literal de cadena a la que se anexa.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[Clase basic_string_view](../standard-library/basic-string-view-class.md)|Una plantilla de clase que proporciona una vista de solo lectura en una secuencia de objetos similares a caracteres arbitrarios.|
|[hash](string-view-hash.md)|Objeto de función que genera un valor hash para un string_view.|

## <a name="requirements"></a>Requisitos

- **Encabezado:** \<string_view >

- **Espacio de nombres:** std

- **Opción del compilador:** std: c ++ 17 (o posterior)

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
