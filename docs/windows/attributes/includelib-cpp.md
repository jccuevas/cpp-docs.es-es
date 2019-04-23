---
title: includelib (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 57f039eeae527dd03884b12e7d9eb424d87f597f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030005"
---
# <a name="includelib-c"></a>includelib (C++)

Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>Parámetros

*name.idl*<br/>
El nombre del archivo .idl que desee incluir como parte del archivo .idl generado.

## <a name="remarks"></a>Comentarios

El **includelib** atributo de C++ hace que un archivo IDL o .h para incluirse en el archivo .idl generado después de la `importlib` instrucción.

## <a name="example"></a>Ejemplo

El código siguiente se muestra en un archivo. cpp:

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
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)