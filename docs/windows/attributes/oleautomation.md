---
title: oleautomation (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.oleautomation
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
ms.openlocfilehash: 201916eeb235d48473d21188da42d19cafb93bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214706"
---
# <a name="oleautomation"></a>oleautomation

Indica que una interfaz es compatible con la automatización.

## <a name="syntax"></a>Sintaxis

```cpp
[oleautomation]
```

## <a name="remarks"></a>Observaciones

El atributo **oleautomation** C++ tiene la misma funcionalidad que el atributo MIDL [oleautomation](/windows/win32/Midl/oleautomation) .

## <a name="example"></a>Ejemplo

Vea los ejemplos de [DefaultValue](defaultvalue.md) y [nonextensible (](nonextensible.md) para ver un ejemplo de uso de **oleautomation**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|**dispinterface**|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)
