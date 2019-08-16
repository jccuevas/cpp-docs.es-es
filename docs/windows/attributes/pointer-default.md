---
title: pointer_default (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: c70c372e5f1c3a9c2f620a1fa3505fb9d0436e79
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514256"
---
# <a name="pointer_default"></a>pointer_default

Especifica el atributo de puntero predeterminado para todos los punteros, excepto los punteros de nivel superior que aparecen en las listas de parámetros.

## <a name="syntax"></a>Sintaxis

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Parámetros

*value*<br/>
Valor que describe el tipo de puntero: **ptr**, **ref**o **único**.

## <a name="remarks"></a>Comentarios

El atributo **pointer_default** C++ tiene la misma funcionalidad que el atributo MIDL [pointer_default](/windows/win32/Midl/pointer-default) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [DefaultValue](defaultvalue.md) para obtener un ejemplo de uso de **pointer_default**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interface**|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)