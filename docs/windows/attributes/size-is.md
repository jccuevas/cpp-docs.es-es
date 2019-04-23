---
title: size_is (C++ atributo COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: a7b990a708bafba78c9dc4153315f8b7b20351ba
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033237"
---
# <a name="sizeis"></a>size_is

Especifique el tamaño de memoria asignada para los punteros de tamaño, tamaño punteros a punteros de tamaño y solo - o matrices multidimensionales.

## <a name="syntax"></a>Sintaxis

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>Parámetros

*expression*<br/>
El tamaño de memoria asignada para un tamaño punteros.

## <a name="remarks"></a>Comentarios

El **size_is** C++ atributo tiene la misma funcionalidad que el [size_is](/windows/desktop/Midl/size-is) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [first_is](first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Campo de **struct** o **unión**, parámetro de interfaz, el método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
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