---
title: propputref (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: e471e467c55e0b8a17be96fd1bcb3cd24cfafe06
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031834"
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

Vea el ejemplo de [enlazable](bindable.md) para un ejemplo de uso de **propputref**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|`propget`, `propput`|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)