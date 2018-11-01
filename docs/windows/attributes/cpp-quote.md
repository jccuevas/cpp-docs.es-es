---
title: cpp_quote (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 5a281f9f88412df4d3ee18bff1302b19433e07f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466955"
---
# <a name="cppquote"></a>cpp_quote

Emite la cadena especificada, sin los caracteres de comillas en el archivo .idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>Parámetros

*statement*<br/>
Una instrucción de C.

## <a name="remarks"></a>Comentarios

El **cpp_quote** atributo de C++ es útil si desea colocar una directiva de preprocesador en un archivo. idl.

También puede usar **cpp_quote** y generar un archivo .h como parte de la compilación de MIDL. Por ejemplo, si tiene un archivo de encabezado de C++ que utiliza atributos IDL de C++, pero no se puede usar este archivo para alguna tarea, a continuación, puede compilar para crear un archivo .h generados por MIDL, que debe ser capaz de usar.

El **cpp_quote** atributo tiene la misma funcionalidad que el [cpp_quote](/windows/desktop/Midl/cpp-quote) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [dual](dual.md) para obtener un ejemplo, usar uso **cpp_quote**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|En cualquier lugar|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)