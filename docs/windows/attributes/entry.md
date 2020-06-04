---
title: entry (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 9bdfc64506f26ee4e9876920821883a0fa12bc7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167100"
---
# <a name="entry"></a>entrada

Especifica una función o una constante exportadas en un módulo mediante la identificación del punto de entrada en el archivo DLL.

## <a name="syntax"></a>Sintaxis

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Parámetros

*id*<br/>
IDENTIFICADOR del punto de entrada.

## <a name="remarks"></a>Observaciones

El atributo de **entrada** C++ tiene la misma funcionalidad que el atributo MIDL de [entrada](/windows/win32/Midl/entry) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [idl_module](idl-module.md) para obtener un ejemplo de uso de **entry**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Atributo `idl_module`|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)
