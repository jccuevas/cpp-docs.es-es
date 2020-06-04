---
title: size_is (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: c511901b3da03d14b1a09e178b70e8f78cd00f8c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166255"
---
# <a name="size_is"></a>size_is

Especifique el tamaño de la memoria asignada para punteros de tamaño, punteros de tamaño a punteros de tamaño y matrices de un solo o multidimensionales.

## <a name="syntax"></a>Sintaxis

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>Parámetros

*expression*<br/>
Tamaño de la memoria asignada para los punteros de tamaño.

## <a name="remarks"></a>Observaciones

El atributo **size_is** C++ tiene la misma funcionalidad que el atributo MIDL [size_is](/windows/win32/Midl/size-is) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [first_is](first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Campo en **struct** o **Union**, parámetro de interfaz, método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|`max_is`|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)
