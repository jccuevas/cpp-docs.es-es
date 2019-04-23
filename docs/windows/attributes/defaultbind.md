---
title: defaultbind (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultbind
helpviewer_keywords:
- defaultbind attribute
ms.assetid: b20a8437-24e6-4b6d-a2df-09fe5e1006e0
ms.openlocfilehash: f0dd9101966f22253e6c4098c3c64d22d0a0cba6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041369"
---
# <a name="defaultbind"></a>defaultbind

Indica la única propiedad enlazable que mejor representa al objeto.

## <a name="syntax"></a>Sintaxis

```cpp
[defaultbind]
```

## <a name="remarks"></a>Comentarios

El **defaultbind** atributo de C++ tiene la misma funcionalidad que el [defaultbind](/windows/desktop/Midl/defaultbind) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [enlazable](bindable.md) para obtener un ejemplo de cómo usar **defaultbind**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[Atributos de miembros de datos](data-member-attributes.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)