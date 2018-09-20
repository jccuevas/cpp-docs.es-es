---
title: Id. | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.id
dev_langs:
- C++
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13ddef5b6bb83de16c72438e2b9f2bb3d4e8d635
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386358"
---
# <a name="id"></a>id

Especifica un *dispid* parámetro para una función miembro (una propiedad o un método en una interfaz o interfaz dispinterface).

## <a name="syntax"></a>Sintaxis

```cpp
[ id(
   dispid
) ]
```

### <a name="parameters"></a>Parámetros

*DISPID*<br/>
El identificador de envío para el método de interfaz.

## <a name="remarks"></a>Comentarios

El **id** atributo de C++ tiene la misma funcionalidad que el [id](/windows/desktop/Midl/id) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [enlazable](../windows/bindable.md) para obtener un ejemplo de cómo usar **id**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de método](../windows/method-attributes.md)<br/>
[Atributos de miembros de datos](../windows/data-member-attributes.md)<br/>
[defaultvalue](../windows/defaultvalue.md)<br/>
[in](../windows/in-cpp.md)<br/>
[out](../windows/out-cpp.md)  