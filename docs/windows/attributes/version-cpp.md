---
title: versión (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: 01c4cca846326d237fdacd19187a44e21bd15913
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519319"
---
# <a name="version-c"></a>version (C++)

Identifica una versión determinada entre varias versiones de una clase.

## <a name="syntax"></a>Sintaxis

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Parámetros

*version*<br/>
El número de versión de la `coclass`. Si no se especifica, se colocará en el archivo .idl 1.0.

## <a name="remarks"></a>Comentarios

El **versión** atributo de C++ tiene la misma funcionalidad que el [versión](/windows/desktop/Midl/version) atributo MIDL y se pasa a través del archivo .idl generado.

## <a name="example"></a>Ejemplo

Consulte la [enlazable](bindable.md) ejemplo para un ejemplo de uso de **versión**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase**|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos de clase](class-attributes.md)