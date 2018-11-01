---
title: restringido (atributo de COM de C++)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 1aa18255f7d7a0740494050a149d436fb167fe8a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521057"
---
# <a name="restricted"></a>restricted

Especifica que un miembro de un módulo, interfaz o dispinterface no se puede llamar arbitrariamente.

## <a name="syntax"></a>Sintaxis

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>Parámetros

*interfaces*<br/>
Una o más interfaces que no se llama de forma arbitraria en un objeto COM. Este parámetro solo es válido cuando se aplica a una clase.

## <a name="remarks"></a>Comentarios

El **restringido** atributo de C++ tiene la misma funcionalidad que el [restringido](/windows/desktop/Midl/restricted) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo usar el **restringido** atributo:

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método, la interfaz **interfaz**, **clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase** (cuando se aplica a **clase** o **struct**)|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de método](method-attributes.md)