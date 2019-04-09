---
title: no_injected_text (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 354643020e704a87daa2e56e923b6a0a704bf0b5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038374"
---
# <a name="noinjectedtext"></a>no_injected_text

Impide que el compilador inserte el código como resultado el uso de atributo.

## <a name="syntax"></a>Sintaxis

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Parámetros

*booleano*<br/>
(Opcional) **true** si no desea que ningún código insertado, **false** para permitir la inserción de código. **True** es el valor predeterminado.

## <a name="remarks"></a>Comentarios

El uso más común de la **no_injected_text** atributo de C++ es mediante la [/Fx](../../build/reference/fx-merge-injected-code.md) opción del compilador, que inserta la **no_injected_text** atributo en el archivo .mrg.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|En cualquier lugar|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)