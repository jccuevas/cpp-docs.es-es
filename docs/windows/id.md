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
ms.openlocfilehash: 7b7ac87241e9089cc8c0152a6d0c3966dc32fa08
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600247"
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

*DISPID*  
El identificador de envío para el método de interfaz.

## <a name="remarks"></a>Comentarios

El **id** atributo de C++ tiene la misma funcionalidad que el [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) atributo MIDL.

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

[Atributos IDL](../windows/idl-attributes.md)  
[Atributos de método](../windows/method-attributes.md)  
[Atributos de miembros de datos](../windows/data-member-attributes.md)  
[defaultvalue](../windows/defaultvalue.md)  
[in](../windows/in-cpp.md)  
[out](../windows/out-cpp.md)  