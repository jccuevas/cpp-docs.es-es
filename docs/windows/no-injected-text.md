---
title: no_injected_text | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.no_injected_text
dev_langs:
- C++
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e63b0b47dcc3f53ecd5af2d51505df844f66437a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599391"
---
# <a name="noinjectedtext"></a>no_injected_text

Impide que el compilador inserte el código como resultado el uso de atributo.

## <a name="syntax"></a>Sintaxis

```cpp
[ no_injected_text(
   boolean
) ];
```

### <a name="parameters"></a>Parámetros

*booleano* (opcional)  
**True** si no desea que ningún código insertado, **false** para permitir la inserción de código. **True** es el valor predeterminado.

## <a name="remarks"></a>Comentarios

El uso más común de la **no_injected_text** atributo de C++ es mediante la [/Fx](../build/reference/fx-merge-injected-code.md) opción del compilador, que inserta la **no_injected_text** atributo en el archivo .mrg.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|En cualquier lugar|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos de compilador](../windows/compiler-attributes.md)  