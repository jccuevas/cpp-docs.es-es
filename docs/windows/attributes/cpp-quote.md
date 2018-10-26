---
title: cpp_quote (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.cpp_quote
dev_langs:
- C++
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e67b839b487f7bb457eeadb0f4d0385b025ebc3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080603"
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