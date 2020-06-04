---
title: include (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: 39f991bb036dce1c50a9d2ee800d3fec65af7c55
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166788"
---
# <a name="include-c"></a>include (C++)

Especifica uno o más archivos de encabezado que se van a incluir en el archivo. idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>Parámetros

*header_file*<br/>
El nombre de un archivo que desea incluir en el archivo. idl generado.

## <a name="remarks"></a>Observaciones

El atributo **include** C++ hace que se coloque una instrucción `#include` debajo de la instrucción `import "docobj.idl"` en el archivo. idl generado.

El atributo **include** C++ tiene la misma funcionalidad que el atributo MIDL [include](/windows/win32/Midl/include) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra un ejemplo de cómo usar **include**. En este ejemplo, el archivo include. h contiene solo una instrucción `#include`.

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
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)
