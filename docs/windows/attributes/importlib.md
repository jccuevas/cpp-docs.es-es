---
title: importlib (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importlib
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
ms.openlocfilehash: 92cf335e5c4754595f2c7af2e1aef30d309d2f5f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514610"
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

El atributo **importlib** C++ hace que `importlib` se coloque una instrucción en el bloque de biblioteca del archivo. idl generado. El atributo **importlib** tiene la misma funcionalidad que el atributo MIDL [importlib](/windows/win32/Midl/importlib) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra un ejemplo de cómo usar **importlib**:

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
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)