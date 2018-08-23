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
ms.openlocfilehash: 17c5742fccdc32396b36d058188f3609caf08791
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586751"
---
# <a name="propget"></a>propget

Especifica una función de descriptor de acceso de propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
[propget]
```

## <a name="remarks"></a>Comentarios

El **propget** atributo de C++ tiene la misma funcionalidad que el [propget](http://msdn.microsoft.com/library/windows/desktop/aa367145) atributo MIDL.

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

[Atributos IDL](../windows/idl-attributes.md)  
[Atributos de método](../windows/method-attributes.md)  
[propput](../windows/propput.md)  
[propputref](../windows/propputref.md)  