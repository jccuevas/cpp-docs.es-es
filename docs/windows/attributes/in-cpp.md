---
title: in (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: e97008d0399764beeca73dbbc5914e4b891df748
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514595"
---
# <a name="in-c"></a>in (C++)

Indica que se va a pasar un parámetro del procedimiento que realiza la llamada al procedimiento llamado.

## <a name="syntax"></a>Sintaxis

```cpp
[in]
```

## <a name="remarks"></a>Comentarios

El atributo **in** C++ tiene la misma funcionalidad que el atributo MIDL [en](/windows/win32/Midl/in) .

## <a name="example"></a>Ejemplo

Vea [enlazable](bindable.md) para obtener un ejemplo de cómo usar **en**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz, método de interfaz|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|**retval**|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)