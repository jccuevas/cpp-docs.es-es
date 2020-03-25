---
title: nonextensible ((C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: 2a1cd4d685e2fd141c6e11feaea488f44a884c80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214705"
---
# <a name="nonextensible"></a>nonextensible

Especifica que la implementación de `IDispatch` solo incluye las propiedades y los métodos enumerados en la descripción de la interfaz y no se puede extender con miembros adicionales en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
[nonextensible]
```

## <a name="remarks"></a>Observaciones

El atributo **nonextensible (** C++ tiene la misma funcionalidad que el atributo MIDL [nonextensible (](/windows/win32/Midl/nonextensible) .

El uso de **nonextensible (** también requiere el atributo [oleautomation](oleautomation.md) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra un uso del atributo **nonextensible (** :

```cpp
// cpp_attr_ref_nonextensible.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export] typedef long HRESULT;

[dual, nonextensible, ms_union, oleautomation,
uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   HRESULT procedure (int i);
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|No|
|**Atributos requeridos**|`dual` y `oleautomation`, o `dispinterface`|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)
