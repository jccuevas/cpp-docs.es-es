---
title: library_block (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.library_block
dev_langs:
- C++
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf4bcdd9290817bb77eeb20f1a014bd537d15d8b
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792367"
---
# <a name="libraryblock"></a>library_block

Coloca una construcción dentro del bloque de biblioteca IDL.

## <a name="syntax"></a>Sintaxis

```cpp
[library_block]
```

## <a name="remarks"></a>Comentarios

Cuando se coloca una construcción dentro del bloque de biblioteca, asegúrese de que se pasarán en la biblioteca de tipos, independientemente de si se hace referencia. De forma predeterminada, solo construcciones modificación el [coclase](coclass.md), [dispinterface](dispinterface.md), y [idl_module](idl-module.md) atributos se colocan en el bloque de biblioteca.

## <a name="example"></a>Ejemplo

En el código siguiente, se coloca una interfaz personalizada dentro del bloque de biblioteca.

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
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, consulte [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)  