---
title: opcional (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.optional
dev_langs:
- C++
helpviewer_keywords:
- optional attribute
ms.assetid: 86656a66-8e11-4589-8e30-9b0f34eeed03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 10bb2f3bf1c15683b770fd9db143153c5e3aa53c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436447"
---
# <a name="optional-c"></a>optional (C++)

Especifica un parámetro opcional para una función miembro.

## <a name="syntax"></a>Sintaxis

```cpp
[optional]
```

## <a name="remarks"></a>Comentarios

El **opcional** atributo de C++ tiene la misma funcionalidad que el [opcional](/windows/desktop/Midl/optional) atributo MIDL.

## <a name="example"></a>Ejemplo

El siguiente código muestra cómo **opcional** podría utilizarse:

```cpp
// cpp_attr_ref_optional.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] long procedure ([in, optional] VARIANT i);
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de parámetro](../windows/parameter-attributes.md)  