---
title: length_is (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.length_is
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
ms.openlocfilehash: 2f252206f6e364b1a87ee3b7b88b14d0ea19bacb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214791"
---
# <a name="length_is"></a>length_is

Especifica el número de elementos de matriz que se van a transmitir.

## <a name="syntax"></a>Sintaxis

```cpp
[ length_is("expression") ]
```

### <a name="parameters"></a>Parámetros

*expression*<br/>
Una o más expresiones del lenguaje C. Se permiten ranuras de argumentos vacías.

## <a name="remarks"></a>Observaciones

El atributo **length_is** C++ tiene la misma funcionalidad que el atributo MIDL [length_is](/windows/win32/Midl/length-is) .

## <a name="example"></a>Ejemplo

Consulte [first_is](first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Campo en **struct** o **Union**, parámetro de interfaz, método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[last_is](last-is.md)<br/>
[size_is](size-is.md)
