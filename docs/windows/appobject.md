---
title: appobject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.appobject
dev_langs:
- C++
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fafdb99296e19318f183b6c0893d9b4e91f0cd7b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422641"
---
# <a name="appobject"></a>appobject

Identifica la coclase como un objeto de aplicación, que está asociado a una aplicación completa .exe e indica que las funciones y propiedades de la coclase están disponibles globalmente en este [biblioteca de tipos](../mfc/automation-clients-using-type-libraries.md).

## <a name="syntax"></a>Sintaxis

```cpp
[appobject]
```

## <a name="remarks"></a>Comentarios

El **appobject** atributo de C++ tiene la misma funcionalidad que el [appobject](/windows/desktop/Midl/appobject) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra una definición de clase simple precedida por un bloque de atributos que incluye **appobject**:

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
|**Reiterativo**|No|
|**Atributos requeridos**|`coclass`|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de clase](../windows/class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)  