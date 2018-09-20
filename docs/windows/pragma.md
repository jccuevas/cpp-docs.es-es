---
title: pragma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pragma
dev_langs:
- C++
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2e6d5d832cd051c8e527b1d161158483d8fcaed1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428764"
---
# <a name="pragma"></a>pragma

Emite la cadena especificada en el archivo .idl generado sin el uso de comillas.

## <a name="syntax"></a>Sintaxis

```cpp
[ pragma(
   pragma_statement
) ];
```

### <a name="parameters"></a>Parámetros

*pragma_statement*<br/>
La pragma que desea entrar en el archivo .idl generado.

## <a name="remarks"></a>Comentarios

El **pragma** atributo de C++ tiene la misma funcionalidad que el [pragma](/windows/desktop/Midl/pragma) atributo MIDL.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_pragma.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[pragma(pack(4))];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A
{
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
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

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos independientes](../windows/stand-alone-attributes.md)<br/>
[pack](../preprocessor/pack.md)  