---
title: entrada (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 703a55ee7c56b64a5b168016770508508bab09e0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036307"
---
# <a name="entry"></a>entry

Especifica una constante o una función exportada de un módulo mediante la identificación de punto de entrada en el archivo DLL.

## <a name="syntax"></a>Sintaxis

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Parámetros

*id*<br/>
El identificador del punto de entrada.

## <a name="remarks"></a>Comentarios

El **entrada** atributo de C++ tiene la misma funcionalidad que el [entrada](/windows/desktop/Midl/entry) atributo MIDL.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [idl_module](idl-module.md) para un ejemplo del uso de **entrada**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|`idl_module` Atributo|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)