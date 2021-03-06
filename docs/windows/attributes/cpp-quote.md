---
title: cpp_quote (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 451313b5bd1eb5011f1175de5c3bcfe6fb054299
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214921"
---
# <a name="cpp_quote"></a>cpp_quote

Emite la cadena especificada, sin los caracteres de Comillas, en el archivo. idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>Parámetros

*instrucción*<br/>
Una instrucción de C.

## <a name="remarks"></a>Observaciones

El atributo **cpp_quote** C++ es útil si desea colocar una directiva de preprocesador en un archivo. idl.

También puede usar **cpp_quote** y generar un archivo. h como parte de la compilación de MIDL. Por ejemplo, si tiene un C++ archivo de encabezado que usa C++ atributos IDL pero no puede usar este archivo para alguna tarea, puede compilarlo para crear un archivo. h generado por MIDL, que debería poder usar.

El atributo **cpp_quote** tiene la misma funcionalidad que el atributo MIDL [cpp_quote](/windows/win32/Midl/cpp-quote) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [dual](dual.md) para obtener un ejemplo de uso de **cpp_quote**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|En cualquier lugar|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)
