---
title: importlib (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importlib
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
ms.openlocfilehash: 451204aae52d884b9cbc81d7e589028f5cfefae5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166814"
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

## <a name="remarks"></a>Observaciones

El atributo **importlib** C++ hace que se coloque una instrucción `importlib` en el bloque de biblioteca del archivo. idl generado. El atributo **importlib** tiene la misma funcionalidad que el atributo MIDL [importlib](/windows/win32/Midl/importlib) .

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
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
