---
title: ID (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 5faf08418771deda3086a434cff6b1900a37e36e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034701"
---
# <a name="id"></a>id

Especifica un *dispid* parámetro para una función miembro (una propiedad o un método en una interfaz o interfaz dispinterface).

## <a name="syntax"></a>Sintaxis

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
El identificador de envío para el método de interfaz.

## <a name="remarks"></a>Comentarios

El **id** atributo de C++ tiene la misma funcionalidad que el [id](/windows/desktop/Midl/id) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [enlazable](bindable.md) para obtener un ejemplo de cómo usar **id**.

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
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)