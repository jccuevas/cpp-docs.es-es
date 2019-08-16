---
title: appobject (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.appobject
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
ms.openlocfilehash: e02cedff70ac32f7edfdb92b240269c34befee7e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490935"
---
# <a name="appobject"></a>appobject

Identifica la coclase como un objeto de aplicación, que está asociado a una aplicación completa. exe e indica que las funciones y propiedades de la coclase están disponibles globalmente en esta [biblioteca de tipos](../../mfc/automation-clients-using-type-libraries.md).

## <a name="syntax"></a>Sintaxis

```cpp
[appobject]
```

## <a name="remarks"></a>Comentarios

El atributo **appobject** C++ tiene la misma funcionalidad que el atributo MIDL [appobject](/windows/win32/Midl/appobject) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra una definición de clase simple precedida por un bloque de atributos que incluye **appobject**:

```cpp
// cpp_attr_ref_appobject.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];

[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]
__interface ICustom {};

[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]
class A : public ICustom {
   int i;
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|Sin|
|**Atributos requeridos**|`coclass`|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)