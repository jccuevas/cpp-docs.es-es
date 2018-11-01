---
title: usesgetlasterror (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: 44a1a55114bcf2466aa5b084f2b53c5457f1a0aa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487027"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Indica que el llamador que si se produce un error al llamar a esa función, a continuación, el llamador puede, a continuación, llamar a `GetLastError` para recuperar el código de error.

## <a name="syntax"></a>Sintaxis

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Comentarios

El **usesgetlasterror** atributo de C++ tiene la misma funcionalidad que el [usesgetlasterror](/windows/desktop/Midl/usesgetlasterror) atributo MIDL.

## <a name="example"></a>Ejemplo

Consulte la [idl_module](idl-module.md) ejemplo para obtener un ejemplo de cómo usar **usesgetlasterror**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**módulo** atributo|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)