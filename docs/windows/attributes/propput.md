---
title: propput (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: c9853b38675abfa0a94a319ac752eb2ef61a48e0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031744"
---
# <a name="propput"></a>propput

Especifica una función de valor de propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
[propput]
```

## <a name="remarks"></a>Comentarios

El **propput** atributo de C++ tiene la misma funcionalidad que el [propput](/windows/desktop/Midl/propput) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [enlazable](bindable.md) para un ejemplo de uso de **propput**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|`propget`, `propputref`|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)