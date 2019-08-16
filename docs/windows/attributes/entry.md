---
title: entry (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 71abf4f183255fa137b43ac9cabd88d15c3fc85d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490903"
---
# <a name="entry"></a>entry

Especifica una función o una constante exportadas en un módulo mediante la identificación del punto de entrada en el archivo DLL.

## <a name="syntax"></a>Sintaxis

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Parámetros

*id*<br/>
IDENTIFICADOR del punto de entrada.

## <a name="remarks"></a>Comentarios

El atributo de **entrada** C++ tiene la misma funcionalidad que el atributo MIDL de [entrada](/windows/win32/Midl/entry) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [idl_module](idl-module.md) para obtener un ejemplo de uso de **entry**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|`idl_module`atribui|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)