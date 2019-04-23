---
title: incluir (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: d9c68601bea4cecd92b371dada5fb086aeb7657f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033702"
---
# <a name="include-c"></a>include (C++)

Especifica uno o varios archivos de encabezado que se incluirán en el archivo .idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>Parámetros

*header_file*<br/>
El nombre de un archivo que desee incluido en el archivo .idl generado.

## <a name="remarks"></a>Comentarios

El **incluyen** hace que el atributo de C++ un `#include` instrucción colocarse debajo el `import "docobj.idl"` instrucción en el archivo .idl generado.

El **incluyen** atributo de C++ tiene la misma funcionalidad que el [incluyen](/windows/desktop/Midl/include) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra un ejemplo de cómo usar **incluyen**. En este ejemplo, el archivo include.h contiene solo un `#include` instrucción.

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|En cualquier lugar|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)