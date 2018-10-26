---
title: local (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: e510e4faa707c954c52ae9daae4c4dc0d4c800dd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057162"
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

Consulte [call_as](call-as.md) para obtener un ejemplo de cómo usar **local**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interfaz**, método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|`dispinterface`|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[call_as](call-as.md)