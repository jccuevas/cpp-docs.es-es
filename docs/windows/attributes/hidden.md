---
title: Hidden (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: 6b420e8f50bd217de460a81f5faaf9583c701376
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168101"
---
# <a name="hidden"></a>hidden

Indica que el elemento existe, pero no se debe mostrar en un explorador orientado al usuario.

## <a name="syntax"></a>Sintaxis

```cpp
[hidden]
```

## <a name="remarks"></a>Observaciones

El atributo **Hidden** C++ tiene la misma funcionalidad que el atributo MIDL [oculto](/windows/win32/Midl/hidden) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [Bindable](bindable.md) para ver un ejemplo de cómo usar **Hidden**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**, **Class**, **struct**, Method, Property|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase** (cuando se aplica a una **clase** o **struct**)|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de método](method-attributes.md)
