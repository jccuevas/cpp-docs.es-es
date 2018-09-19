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
ms.openlocfilehash: a40ad39b089ea68209bfef2997f015c355ca6893
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414048"
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

*identificador*<br/>
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