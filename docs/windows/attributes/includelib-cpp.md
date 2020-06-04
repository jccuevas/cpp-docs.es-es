---
title: includelib ((C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 4022a3f1f2d4ccaabe65c24065be8e1c846d604d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214855"
---
# <a name="includelib-c"></a>includelib (C++)

Hace que un archivo. idl o. h se incluya en el archivo. idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>Parámetros

*nombre. idl*<br/>
Nombre del archivo. idl que desea incluir como parte del archivo. idl generado.

## <a name="remarks"></a>Observaciones

El atributo **includelib (** C++ hace que un archivo. idl o. h se incluya en el archivo. idl generado, después de la instrucción `importlib`.

## <a name="example"></a>Ejemplo

El siguiente código se muestra en un archivo. cpp:

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|En cualquier lugar|
|**Reiterativo**|Sí|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)
