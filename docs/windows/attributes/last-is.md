---
title: last_is (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.last_is
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
ms.openlocfilehash: 62377415dc0809033fcdcb8bd4e7997f667c1691
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214817"
---
# <a name="last_is"></a>last_is

Especifica el índice del último elemento de la matriz que se va a transmitir.

## <a name="syntax"></a>Sintaxis

```cpp
[ last_is("expression") ]
```

### <a name="parameters"></a>Parámetros

*expression*<br/>
Una o más expresiones del lenguaje C. Se permiten ranuras de argumentos vacías.

## <a name="remarks"></a>Observaciones

El atributo **last_is** C++ tiene la misma funcionalidad que el atributo MIDL [last_is](/windows/win32/Midl/last-is) .

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
[length_is](length-is.md)<br/>
[size_is](size-is.md)
