---
title: ReadOnly (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.readonly
dev_langs:
- C++
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93a7adbca8c659a757e0e8fbb05b8fb926b237d2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210315"
---
# <a name="readonly-c"></a>readonly (C++)

Prohíbe la asignación a un miembro de datos.

## <a name="syntax"></a>Sintaxis

```cpp
[readonly]
```

## <a name="remarks"></a>Comentarios

El **readonly** atributo de C++ tiene la misma funcionalidad que el [readonly](/windows/desktop/Midl/readonly) atributo MIDL.

Si quiere prohibir la modificación de un parámetro de método, use el atributo [in](../windows/in-cpp.md) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra el uso del atributo **readonly** :

```cpp
// cpp_attr_ref_readonly.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]
__interface IFireTabCtrl
{
   [readonly, id(1)] int i();
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)  
[Atributos de miembros de datos](../windows/data-member-attributes.md)  