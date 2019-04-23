---
title: length_is (C++ atributo COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.length_is
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
ms.openlocfilehash: 1de168606b57c801bc3dc1fb9aee76eb6f3d54c8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039915"
---
# <a name="lengthis"></a>length_is

Especifica el número de elementos de matriz que se transmitan.

## <a name="syntax"></a>Sintaxis

```cpp
[ length_is("expression") ]
```

### <a name="parameters"></a>Parámetros

*expression*<br/>
Una o varias expresiones de lenguaje C. Se permiten las ranuras de argumentos vacía.

## <a name="remarks"></a>Comentarios

El **length_is** C++ atributo tiene la misma funcionalidad que el [length_is](/windows/desktop/Midl/length-is) atributo MIDL.

## <a name="example"></a>Ejemplo

Consulte [first_is](first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Campo de **struct** o **unión**, parámetro de interfaz, el método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[last_is](last-is.md)<br/>
[size_is](size-is.md)