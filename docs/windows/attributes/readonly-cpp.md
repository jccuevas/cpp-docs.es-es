---
title: ReadOnly (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.readonly
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
ms.openlocfilehash: d174399b213bc6c8dbaeb0a01f3e457cfcf3a3e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653042"
---
# <a name="readonly-c"></a>readonly (C++)

Prohíbe la asignación a un miembro de datos.

## <a name="syntax"></a>Sintaxis

```cpp
[readonly]
```

## <a name="remarks"></a>Comentarios

El atributo de C++ **readonly** tiene la misma funcionalidad que el atributo MIDL [readonly](/windows/desktop/Midl/readonly) .

Si quiere prohibir la modificación de un parámetro de método, use el atributo [in](in-cpp.md) .

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

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de miembros de datos](data-member-attributes.md)