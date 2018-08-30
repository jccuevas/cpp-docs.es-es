---
title: entrada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95875eaea7206cbfb4ded271e329f10d7aee13fe
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221896"
---
# <a name="entry"></a>entry

Especifica una constante o una función exportada de un módulo mediante la identificación de punto de entrada en el archivo DLL.

## <a name="syntax"></a>Sintaxis

```cpp
[ entry(
   id
) ]
```

### <a name="parameters"></a>Parámetros

*identificador*  
El identificador del punto de entrada.

## <a name="remarks"></a>Comentarios

El **entrada** atributo de C++ tiene la misma funcionalidad que el [entrada](/windows/desktop/Midl/entry) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [idl_module](../windows/idl-module.md) para un ejemplo del uso de **entrada**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Atributo `idl_module`|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)  