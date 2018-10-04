---
title: importlib (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importlib
dev_langs:
- C++
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd43dd8a0fb4660cbe0c631bcb3477ef3d26f0f6
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792463"
---
# <a name="importlib"></a>importlib

Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.

## <a name="syntax"></a>Sintaxis

```cpp
[ importlib("tlb_file") ];
```

### <a name="parameters"></a>Parámetros

*tlb_file*<br/>
El nombre de un archivo .tlb, entre comillas, que desea importar en la biblioteca de tipos del proyecto actual.

## <a name="remarks"></a>Comentarios

El **importlib** hace que el atributo de C++ un `importlib` instrucción que se colocarán en el bloque de biblioteca del archivo .idl generado. El **importlib** atributo tiene la misma funcionalidad que el [importlib](/windows/desktop/Midl/importlib) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra un ejemplo de cómo usar **importlib**:

```cpp
// cpp_attr_ref_importlib.cpp
// compile with: /LD
[module(name="MyLib")];
[importlib("importlib.tlb")];
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|En cualquier lugar|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, consulte [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)