---
title: oculto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.hidden
dev_langs:
- C++
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 350f1c7c844bd386191b2a236f5bc4ada4e1672a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204533"
---
# <a name="hidden"></a>hidden

Indica que el elemento existe pero no debe mostrarse en un explorador orientado al usuario.

## <a name="syntax"></a>Sintaxis

```cpp
[hidden]
```

## <a name="remarks"></a>Comentarios

El **oculto** atributo de C++ tiene la misma funcionalidad que el [oculto](/windows/desktop/Midl/hidden) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [enlazable](../windows/bindable.md) para obtener un ejemplo de cómo usar **oculto**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interfaz**, **clase**, **struct**, método, propiedad|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase** (cuando se aplica a **clase** o **struct**)|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)  
[Atributos de interfaz](../windows/interface-attributes.md)  
[Atributos de clase](../windows/class-attributes.md)  
[Atributos de método](../windows/method-attributes.md)  