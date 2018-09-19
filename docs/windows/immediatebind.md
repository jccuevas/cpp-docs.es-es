---
title: immediatebind | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.immediatebind
dev_langs:
- C++
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd546f6d3eb3b2eae60b4bbc8c8fa9b0b4ed00f1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201030"
---
# <a name="immediatebind"></a>immediatebind

Indica que la base de datos será notificada inmediatamente de todos los cambios a una propiedad de un objeto enlazado a datos.

## <a name="syntax"></a>Sintaxis

```cpp
[immediatebind]
```

## <a name="remarks"></a>Comentarios

El **immediatebind** atributo de C++ tiene la misma funcionalidad que el [immediatebind](/windows/desktop/Midl/immediatebind) atributo MIDL.

## <a name="example"></a>Ejemplo

Consulte [enlazable](../windows/bindable.md) para obtener un ejemplo de cómo usar **immediatebind**.

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
[defaultbind](../windows/defaultbind.md)  
[displaybind](../windows/displaybind.md)  
[requestedit](../windows/requestedit.md)  