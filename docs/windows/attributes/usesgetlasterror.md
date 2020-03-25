---
title: usesgetlasterror (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: f58929db01a1710e811a973c0559ad29b242b4eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166138"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Indica al llamador que, si se produce un error al llamar a esa función, el llamador puede llamar a `GetLastError` para recuperar el código de error.

## <a name="syntax"></a>Sintaxis

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Observaciones

El atributo **usesgetlasterror** C++ tiene la misma funcionalidad que el atributo MIDL [usesgetlasterror](/windows/win32/Midl/usesgetlasterror) .

## <a name="example"></a>Ejemplo

Vea el [idl_module](idl-module.md) ejemplo para obtener un ejemplo de cómo usar **usesgetlasterror**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**Module** (atributo)|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)
