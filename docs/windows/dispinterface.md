---
title: dispinterface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dispinterface
dev_langs:
- C++
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a98c9016281a67211a41d1c63fcb9886a0b3c35
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222515"
---
# <a name="dispinterface"></a>dispinterface

Coloca una interfaz en el archivo .idl como interfaz de envío.

## <a name="syntax"></a>Sintaxis

```cpp
[dispinterface]
```

## <a name="remarks"></a>Comentarios

Cuando el atributo de C++ **dispinterface** precede a una interfaz, hace que esta se coloque dentro del bloque de biblioteca del archivo .idl generado.

A menos que especifique una clase base, se derivará una interfaz de envío de `IDispatch`. Debe especificar un [id](../windows/id.md) para los miembros de una interfaz de envío.

El ejemplo de uso de [dispinterface](/windows/desktop/Midl/dispinterface) en la documentación de MIDL:

```cpp
dispinterface helloPro
   { interface hello; };
```

no es válido para el atributo **dispinterface** .

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [bindable](../windows/bindable.md) para ver un ejemplo de cómo usar **dispinterface**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)  
[Atributos por uso](../windows/attributes-by-usage.md)  
[uuid](../windows/uuid-cpp-attributes.md)  
[dual](../windows/dual.md)  
[Personalizado](../windows/custom-cpp.md)  
[object](../windows/object-cpp.md)  
[__interface](../cpp/interface.md)  