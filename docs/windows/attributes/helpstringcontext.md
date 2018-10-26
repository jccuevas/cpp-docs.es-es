---
title: helpstringcontext (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringcontext
dev_langs:
- C++
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 00b0e7824de3c6977bd641e7016e3efc5acdcfa1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067377"
---
# <a name="helpstringcontext"></a>helpstringcontext

Especifica el identificador de un tema de ayuda en un archivo .hlp o chm.

## <a name="syntax"></a>Sintaxis

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>Parámetros

*contextID*<br/>
Un identificador de contexto de Ayuda de 32 bits en el **ayuda** archivo.

## <a name="remarks"></a>Comentarios

El **helpstringcontext** atributo de C++ tiene la misma funcionalidad que el [helpstringcontext](/windows/desktop/Midl/helpstringcontext) ODL (atributo).

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_helpstringcontext.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[   object, helpstring("help string"), helpstringcontext(1), uuid="11111111-1111-1111-1111-111111111111"
]
__interface IMyI
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **interfaz**, método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[module](module-cpp.md)