---
title: Restricted (C++ atributo com)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: a47c56673e19f891b24ff433b9c614804f0bd51c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166372"
---
# <a name="restricted"></a>restricted

Especifica que no se puede llamar a un miembro de un módulo, interfaz o dispinterface arbitrariamente.

## <a name="syntax"></a>Sintaxis

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>Parámetros

*interfaces*<br/>
Una o más interfaces a las que no se puede llamar arbitrariamente en un objeto COM. Este parámetro solo es válido cuando se aplica a una clase.

## <a name="remarks"></a>Observaciones

El atributo **Restricted** C++ tiene la misma funcionalidad que el atributo MIDL [restringido](/windows/win32/Midl/restricted) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo usar el atributo **Restricted** :

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
|**Se aplica a**|Método de interfaz, **interfaz**, **clase**, **estructura**|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase** (cuando se aplica a una **clase** o **struct**)|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de método](method-attributes.md)
