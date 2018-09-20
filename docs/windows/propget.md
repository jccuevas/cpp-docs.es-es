---
title: propget | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propget
dev_langs:
- C++
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d5a145c730104608bd8b1709191fef32d3bfc08
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380760"
---
# <a name="propget"></a>propget

Especifica una función de descriptor de acceso de propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
[propget]
```

## <a name="remarks"></a>Comentarios

El **propget** atributo de C++ tiene la misma funcionalidad que el [propget](/windows/desktop/Midl/propget) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [enlazable](../windows/bindable.md) para un ejemplo de uso de **propget**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|`propput`, `propputref`|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de método](../windows/method-attributes.md)<br/>
[propput](../windows/propput.md)<br/>
[propputref](../windows/propputref.md)  