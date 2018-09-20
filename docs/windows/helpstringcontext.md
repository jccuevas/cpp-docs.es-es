---
title: helpstringcontext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 47afe841a2a8e4a1c41baf68dfd139a70b320c7d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394470"
---
# <a name="helpstringcontext"></a>helpstringcontext

Especifica el identificador de un tema de ayuda en un archivo .hlp o chm.

## <a name="syntax"></a>Sintaxis

```cpp
[ helpstringcontext(
   contextID
) ]
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

[   object,
   helpstring("help string"),
   helpstringcontext(1),
   uuid="11111111-1111-1111-1111-111111111111"
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

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de interfaz](../windows/interface-attributes.md)<br/>
[Atributos de clase](../windows/class-attributes.md)<br/>
[Atributos de método](../windows/method-attributes.md)<br/>
[módulo](../windows/module-cpp.md)  