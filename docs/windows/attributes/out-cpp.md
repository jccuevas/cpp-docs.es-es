---
title: out (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: 6ab8fdf691e2220087f5c5d64bb70c5deb27675c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214707"
---
# <a name="out-c"></a>out (C++)

Identifica los parámetros de puntero devueltos desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).

## <a name="syntax"></a>Sintaxis

```cpp
[out]
```

## <a name="remarks"></a>Observaciones

El atributo de C++ **out** tiene la misma funcionalidad que el atributo MIDL [out](/windows/win32/Midl/out-idl) .

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [bindable](bindable.md) para ver un ejemplo de uso de **out**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)
