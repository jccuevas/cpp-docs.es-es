---
title: propputref | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propputref
dev_langs:
- C++
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2afa793371f2e9840bbb98efc9f745ecbdd29b7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389335"
---
# <a name="propputref"></a>propputref

Especifica una función de la configuración de propiedad que utiliza una referencia en lugar de un valor.

## <a name="syntax"></a>Sintaxis

```cpp
[propputref]
```

## <a name="remarks"></a>Comentarios

El **propputref** atributo de C++ tiene la misma funcionalidad que el [propputref](/windows/desktop/Midl/propputref) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [enlazable](../windows/bindable.md) para un ejemplo de uso de **propputref**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|`propget`, `propput`|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de método](../windows/method-attributes.md)<br/>
[propget](../windows/propget.md)<br/>
[propput](../windows/propput.md)  