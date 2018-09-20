---
title: local (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.local
dev_langs:
- C++
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0b45106609c4bc93684e0d89737bb0753e36fb4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421094"
---
# <a name="local-c"></a>local (C++)

Cuando se utiliza en el encabezado de la interfaz, permite usar el compilador de MIDL como un generador de encabezado. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.

## <a name="syntax"></a>Sintaxis

```cpp
[local]
```

## <a name="remarks"></a>Comentarios

El **local** atributo de C++ tiene la misma funcionalidad que el [local](/windows/desktop/Midl/local) atributo MIDL.

## <a name="example"></a>Ejemplo

Consulte [call_as](../windows/call-as.md) para obtener un ejemplo de cómo usar **local**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interfaz**, método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|`dispinterface`|

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de interfaz](../windows/interface-attributes.md)<br/>
[Atributos de método](../windows/method-attributes.md)<br/>
[call_as](../windows/call-as.md)  