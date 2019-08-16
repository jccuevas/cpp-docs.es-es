---
title: Hidden (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: 75b03877b1204d6e1c4770f5ba9c8c88338b3394
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501447"
---
# <a name="hidden"></a>hidden

Indica que el elemento existe, pero no se debe mostrar en un explorador orientado al usuario.

## <a name="syntax"></a>Sintaxis

```cpp
[hidden]
```

## <a name="remarks"></a>Comentarios

El atributo **Hidden** C++ tiene la misma funcionalidad que el atributo MIDL [oculto](/windows/win32/Midl/hidden) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [Bindable](bindable.md) para ver un ejemplo de cómo usar **Hidden**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**, **Class**, **struct**, Method, Property|
|**Reiterativo**|Sin|
|**Atributos requeridos**|**coclase** (cuando se aplica a la **clase** o **struct**)|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de método](method-attributes.md)