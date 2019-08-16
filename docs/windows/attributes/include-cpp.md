---
title: include (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: ece88ebd7b5d9d81beb871427b58a72b2cf02022
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514555"
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

## <a name="remarks"></a>Comentarios

El atributo **include** C++ hace que `#include` se coloque una instrucción debajo de `import "docobj.idl"` la instrucción en el archivo. idl generado.

El atributo **include** C++ tiene la misma funcionalidad que el atributo MIDL [include](/windows/win32/Midl/include) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra un ejemplo de cómo usar **include**. En este ejemplo, el archivo include. h contiene solo una `#include` instrucción.

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
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)