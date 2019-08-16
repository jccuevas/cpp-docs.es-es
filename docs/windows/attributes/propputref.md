---
title: PROPPUTREF (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: 9dc21494886f80890bcfde7f29bb3d6c86b4a51b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514189"
---
# <a name="propputref"></a>propputref

Especifica una función de configuración de propiedades que usa una referencia en lugar de un valor.

## <a name="syntax"></a>Sintaxis

```cpp
[propputref]
```

## <a name="remarks"></a>Comentarios

El atributo **PROPPUTREF** C++ tiene la misma funcionalidad que el atributo MIDL de la [PROPPUTREF](/windows/win32/Midl/propputref) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [Bindable](bindable.md) para ver un ejemplo de uso de **PROPPUTREF**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|`propget`, `propput`|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)