---
title: oleautomation (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.oleautomation
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
ms.openlocfilehash: 56970d8b1067e1ac38230b6995074210ddc5549b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514365"
---
# <a name="oleautomation"></a>oleautomation

Indica que una interfaz es compatible con la automatización.

## <a name="syntax"></a>Sintaxis

```cpp
[oleautomation]
```

## <a name="remarks"></a>Comentarios

El atributo **oleautomation** C++ tiene la misma funcionalidad que el atributo MIDL [oleautomation](/windows/win32/Midl/oleautomation) .

## <a name="example"></a>Ejemplo

Vea los ejemplos de [DefaultValue](defaultvalue.md) y [nonextensible (](nonextensible.md) para ver un ejemplo de uso de **oleautomation**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|**dispinterface**|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)