---
title: local (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: 377d6ffbddb5f88533c8b4f054f0d658a9b19573
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489094"
---
# <a name="local-c"></a>local (C++)

Cuando se utiliza en el encabezado de la interfaz, permite usar el compilador de MIDL como un generador de encabezado. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.

## <a name="syntax"></a>Sintaxis

```cpp
[local]
```

## <a name="remarks"></a>Comentarios

El **local** atributo de C++ tiene la misma funcionalidad que el [local](/windows/desktop/Midl/local) atributo MIDL.

## <a name="example"></a>Ejemplo

Consulte [call_as](call-as.md) para obtener un ejemplo de cómo usar **local**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**interfaz**, método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|`dispinterface`|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[call_as](call-as.md)