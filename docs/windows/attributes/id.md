---
title: ID (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 79e49b2c074cd82323c74489e33812c10c442c61
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168062"
---
# <a name="id"></a>id

Especifica un parámetro de *DISPID* para una función miembro (ya sea una propiedad o un método, en una interfaz o dispinterface).

## <a name="syntax"></a>Sintaxis

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Parámetros

*DISPID*<br/>
IDENTIFICADOR de envío del método de interfaz.

## <a name="remarks"></a>Observaciones

El atributo **ID** C++ tiene la misma funcionalidad que el atributo MIDL [ID](/windows/win32/Midl/id) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [Bindable](bindable.md) para ver un ejemplo de cómo usar **ID**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[Atributos de miembros de datos](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)
