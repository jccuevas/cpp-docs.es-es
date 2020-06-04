---
title: versión (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: e5fcf80ef753a869b8798d6ab9c8e9f8ecff16fd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165995"
---
# <a name="version-c"></a>version (C++)

Identifica una versión concreta entre varias versiones de una clase.

## <a name="syntax"></a>Sintaxis

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Parámetros

*version*<br/>
El número de versión de `coclass`. Si no se especifica, 1,0 se colocará en el archivo. idl.

## <a name="remarks"></a>Observaciones

El atributo **version** C++ tiene la misma funcionalidad que el atributo MIDL de la [versión](/windows/win32/Midl/version) y se pasa a través del archivo. idl generado.

## <a name="example"></a>Ejemplo

Vea el ejemplo [enlazable](bindable.md) para obtener un ejemplo de uso de la **versión**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclass**|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos de clase](class-attributes.md)
