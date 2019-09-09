---
title: versión (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: 9a432267632b1f2a716a833a485b182cd93a27e2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514876"
---
# <a name="version-c"></a>version (C++)

Identifica una versión concreta entre varias versiones de una clase.

## <a name="syntax"></a>Sintaxis

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Parámetros

*version*<br/>
Número de versión del `coclass`. Si no se especifica, 1,0 se colocará en el archivo. idl.

## <a name="remarks"></a>Comentarios

El atributo **version** C++ tiene la misma funcionalidad que el atributo MIDL de la [versión](/windows/win32/Midl/version) y se pasa a través del archivo. idl generado.

## <a name="example"></a>Ejemplo

Vea el ejemplo [enlazable](bindable.md) para obtener un ejemplo de uso de la **versión**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|Sin|
|**Atributos requeridos**|**coclase**|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos de clase](class-attributes.md)