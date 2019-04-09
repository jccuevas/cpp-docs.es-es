---
title: max_is (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: dca2a3dc18aa3c3e75bbb682ed0b1b90adcd9236
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041314"
---
# <a name="maxis"></a>max_is

Designa el valor máximo para un índice de matriz válida.

## <a name="syntax"></a>Sintaxis

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>Parámetros

*expresión*<br/>
Una o varias expresiones de lenguaje C. Se permiten las ranuras de argumentos vacía.

## <a name="remarks"></a>Comentarios

El **max_is** atributo de C++ tiene la misma funcionalidad que el [max_is](/windows/desktop/Midl/max-is) atributo MIDL.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Campo de **struct** o **unión**, parámetro de interfaz, el método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|**size_is**|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Ejemplo

Consulte [first_is](first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (Atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)