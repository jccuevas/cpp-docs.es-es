---
title: library_block | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 33febb69db2a8f3bd67205de2e6e5cf019016471
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598498"
---
# <a name="libraryblock"></a>library_block

Coloca una construcción dentro del bloque de biblioteca IDL.

## <a name="syntax"></a>Sintaxis

```cpp
[library_block]
```

## <a name="remarks"></a>Comentarios

Cuando se coloca una construcción dentro del bloque de biblioteca, asegúrese de que se pasarán en la biblioteca de tipos, independientemente de si se hace referencia. De forma predeterminada, solo construcciones modificación el [coclase](../windows/coclass.md), [dispinterface](../windows/dispinterface.md), y [idl_module](../windows/idl-module.md) atributos se colocan en el bloque de biblioteca.

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

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos de compilador](../windows/compiler-attributes.md)  
[Atributos independientes](../windows/stand-alone-attributes.md)  