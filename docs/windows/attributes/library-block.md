---
title: library_block (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.library_block
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
ms.openlocfilehash: 405cc1cd5af7dcd689e833764f3da2fdc6d5f703
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214778"
---
# <a name="library_block"></a>library_block

Coloca una construcción dentro del bloque de la biblioteca IDL.

## <a name="syntax"></a>Sintaxis

```cpp
[library_block]
```

## <a name="remarks"></a>Observaciones

Cuando se coloca una construcción dentro del bloque de biblioteca, se garantiza que se pasará a la biblioteca de tipos, independientemente de si se hace referencia a ella. De forma predeterminada, solo las construcciones modificadas por los atributos [CoClass](coclass.md), [dispinterface](dispinterface.md)y [idl_module](idl-module.md) se colocan en el bloque de biblioteca.

## <a name="example"></a>Ejemplo

En el código siguiente, una interfaz personalizada se coloca dentro del bloque de biblioteca.

```cpp
// cpp_attr_ref_library_block.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib")];
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface IMyInterface {
   HRESULT f1();
};
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
[Atributos independientes](stand-alone-attributes.md)
