---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 47924c3d6bd1a2f45cdbac648f4f563c57ce8939
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459116"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

Define la plantilla `basic_string_view` de clase y los tipos y operadores relacionados. (Requiere la opción del compilador [STD: c++ 17](../build/reference/std-specify-language-standard-version.md) o posterior).

## <a name="syntax"></a>Sintaxis

```cpp
#include <string_view>
```

## <a name="remarks"></a>Comentarios

La familia string_view de especializaciones de plantilla proporciona una manera eficaz de pasar un identificador no propietario de solo lectura, seguro para excepciones, a los datos de caracteres de cualquier objeto similar a una cadena con el primer elemento de la secuencia en la posición cero. Un parámetro de función de `string_view` tipo (que es una definición `basic_string_view<char>`de tipos para) `std::string`puede aceptar argumentos como, **Char\*** o cualquier otra clase similar a una cadena de caracteres estrechos para los que una conversión `string_view`implícitaestá definido. De forma similar, un `wstring_view`parámetro `u16string_view` de `u32string_view` o puede aceptar cualquier tipo de cadena para el que se define una conversión implícita. Para obtener más información, consulte [clase basic_string_view](../standard-library/basic-string-view-class.md).

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|DESCRIPCIÓN|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Una especialización de la plantilla `basic_string_view` de clase con elementos de tipo **Char**.|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Una especialización de la plantilla `basic_string_view` de clase con elementos de tipo **wchar_t**.|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|Una especialización de la plantilla `basic_string_view` de clase con elementos de tipo. `char16_t`|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|Una especialización de la plantilla `basic_string_view` de clase con elementos de tipo. `char32_t`|

### <a name="operators"></a>Operadores

Los \<operadores string_view > pueden comparar `string_view` objetos con objetos de cualquier tipo de cadena convertible.

|Operador|DESCRIPCIÓN|
|-|-|
|[operator!=](../standard-library/string-view-operators.md#op_neq)|Comprueba si el objeto en el lado izquierdo del operador no es igual al objeto del lado derecho.|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|Comprueba si el objeto en el lado izquierdo del operador es igual al objeto del lado derecho.|
|[operator<](../standard-library/string-view-operators.md#op_lt)|Comprueba si el objeto en el lado izquierdo del operador es menor que el objeto del lado derecho.|
|[operator<=](../standard-library/string-view-operators.md#op_lt_eq)|Comprueba si el objeto en el lado izquierdo del operador es menor o igual que el objeto del lado derecho.|
|[operator<\<](../standard-library/string-view-operators.md#op_lt_lt)|Una función de plantilla que inserta un `string_view` en un flujo de salida.|
|[operator>](../standard-library/string-view-operators.md#op_gt)|Comprueba si el objeto en el lado izquierdo del operador es mayor que el objeto del lado derecho.|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|Comprueba si el objeto en el lado izquierdo del operador es mayor o igual que el objeto del lado derecho.|

### <a name="literals"></a>Literales

|Operador|DESCRIPCIÓN|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|`string_view`Construye, `wstring_view`, `u16string_view`o ,dependiendodeltipodelliteraldecadenaalqueseanexa.`u32string_view`|

### <a name="classes"></a>Clases

|Clase|DESCRIPCIÓN|
|-|-|
|[Clase basic_string_view](../standard-library/basic-string-view-class.md)|Una plantilla de clase que proporciona una vista de solo lectura en una secuencia de objetos arbitrarios similares a caracteres.|
|[hash](string-view-hash.md)|Objeto de función que genera un valor hash para un string_view.|

## <a name="requirements"></a>Requisitos

- **Encabezado:** \<> string_view

- **Espacio de nombres:** std

- **Opción del compilador:** STD: c++ 17 (o posterior)

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
