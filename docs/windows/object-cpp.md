---
title: objeto (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e1cf7f100c34023e6fea96c9764cce2371dcaaf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412697"
---
# <a name="object-c"></a>object (C++)

Identifica una interfaz personalizada.

## <a name="syntax"></a>Sintaxis

```cpp
[object]
```

## <a name="remarks"></a>Comentarios

Cuando precede a una definición de interfaz, el **objeto** la interfaz que se colocarán en el archivo .idl como una interfaz personalizada hace que el atributo de C++.

Cualquier interfaz marcada con el objeto debe heredar de `IUnknown`. Esta condición se cumple si cualquiera de las interfaces bases se hereda de `IUnknown`. Si no hay interfaces bases se heredan de `IUnknown`, el compilador hará que la interfaz marcada con **objeto** derivar `IUnknown`.

## <a name="example"></a>Ejemplo

Consulte [nonbrowsable](../windows/nonbrowsable.md) para obtener un ejemplo de cómo usar **objeto**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de interfaz](../windows/interface-attributes.md)<br/>
[dual](../windows/dual.md)<br/>
[dispinterface](../windows/dispinterface.md)<br/>
[Personalizado](../windows/custom-cpp.md)<br/>
[__interface](../cpp/interface.md)  