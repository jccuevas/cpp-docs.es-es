---
title: importidl (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 6e41a98bef079c92b6df6e7eff203301aa9ceae4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166827"
---
# <a name="importidl"></a>importidl

Inserta el archivo. idl especificado en el archivo. idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>Parámetros

*idl_file*<br/>
Identifica el nombre del archivo. idl que desea combinar con el archivo. idl que se generará para la aplicación.

## <a name="remarks"></a>Observaciones

El atributo **importidl** C++ coloca la sección fuera del bloque de biblioteca (en *idl_file*) en el archivo. idl generado del programa y la sección Library (en *idl_file*) en la sección Library del archivo. idl generado del programa.

Puede que desee usar **importidl**, por ejemplo, si desea utilizar un archivo. idl codificado a mano con el archivo. idl generado.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
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

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
