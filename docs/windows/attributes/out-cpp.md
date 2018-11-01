---
title: out (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: 15b82ddca42f9b70ac16538cea19f8aedd799c05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574452"
---
# <a name="out-c"></a>out (C++)

Identifica los parámetros de puntero devueltos desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).

## <a name="syntax"></a>Sintaxis

```cpp
[out]
```

## <a name="remarks"></a>Comentarios

El atributo de C++ **out** tiene la misma funcionalidad que el atributo MIDL [out](/windows/desktop/Midl/out-idl) .

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [bindable](bindable.md) para ver un ejemplo de uso de **out**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[identificador](id.md)