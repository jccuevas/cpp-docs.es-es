---
title: size_is (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: 504f1bf72b8ffa15e8df50bb00c86ef909688f1e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514032"
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

## <a name="remarks"></a>Comentarios

El atributo **size_is** C++ tiene la misma funcionalidad que el atributo MIDL de [size_is](/windows/win32/Midl/size-is) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [first_is](first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Campo en **struct** o **Union**, parámetro de interfaz, método de interfaz|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|`max_is`|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)