---
title: oleautomation (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.oleautomation
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
ms.openlocfilehash: 4a50121e1a2e170ba69ee21526f4600512097c74
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471674"
---
# <a name="oleautomation"></a>oleautomation

Indica que una interfaz es compatible con la automatización.

## <a name="syntax"></a>Sintaxis

```cpp
[oleautomation]
```

## <a name="remarks"></a>Comentarios

El **oleautomation** atributo de C++ tiene la misma funcionalidad que el [oleautomation](/windows/desktop/Midl/oleautomation) atributo MIDL.

## <a name="example"></a>Ejemplo

Consulte los ejemplos de [defaultvalue](defaultvalue.md) y [nonextensible](nonextensible.md) para un ejemplo de uso de **oleautomation**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|**dispinterface**|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)