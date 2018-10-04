---
title: includelib (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6be5bb96f819bf1f1b0ba90d345a3c2d312daeea
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792490"
---
# <a name="includelib-c"></a>includelib (C++)

Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>Parámetros

*Name.idl*<br/>
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

Para obtener más información, consulte [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)  