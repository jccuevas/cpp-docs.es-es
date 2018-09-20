---
title: incluir (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.include
dev_langs:
- C++
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 617747a9eda77d8dc2ba21006b649daead9546d3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419326"
---
# <a name="include-c"></a>include (C++)

Especifica uno o varios archivos de encabezado que se incluirán en el archivo .idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ include(
   header_file
) ];
```

### <a name="parameters"></a>Parámetros

*HEADER_FILE*<br/>
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

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos independientes](../windows/stand-alone-attributes.md)<br/>
[import](../windows/import.md)<br/>
[importidl](../windows/importidl.md)<br/>
[includelib](../windows/includelib-cpp.md)<br/>
[importlib](../windows/importlib.md)  