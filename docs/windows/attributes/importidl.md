---
title: importidl (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 8d0d891f74da8df2351b0a861fb7501e72f5e2de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587179"
---
# <a name="importidl"></a>importidl

Inserta el archivo .idl especificado en el archivo .idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>Parámetros

*idl_file*<br/>
Identifica el nombre del archivo .idl que desea combinar con el archivo .idl que se generará para la aplicación.

## <a name="remarks"></a>Comentarios

El **importidl** atributo de C++ coloca la sección fuera del bloque de biblioteca (en *idl_file*) en el archivo .idl generado del programa y la sección de biblioteca (en *idl_file*) en la biblioteca de la sección de su programa genera el archivo .idl.

Es posible que desee usar **importidl**, por ejemplo, si desea usar un archivo .idl codificadas con el archivo .idl generado.

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
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)