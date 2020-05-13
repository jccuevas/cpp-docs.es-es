---
title: no_injected_text (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 5f98be3478b2e1eeb4b464f1784f3f4ece22d8a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166619"
---
# <a name="no_injected_text"></a>no_injected_text

Impide que el compilador Inserte código como resultado del uso de atributos.

## <a name="syntax"></a>Sintaxis

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Parámetros

*boolean*<br/>
Opta **true** si desea que no se inserte código, **false** para permitir que se inserte código. **true** es el valor predeterminado.

## <a name="remarks"></a>Observaciones

El uso más común del atributo **no_injected_text** C++ es mediante la opción del compilador [/FX](../../build/reference/fx-merge-injected-code.md) , que inserta el atributo **no_injected_text** en el archivo. MRG.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|En cualquier lugar|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos de compilador](compiler-attributes.md)
