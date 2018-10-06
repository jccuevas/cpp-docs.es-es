---
title: personalizado (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.custom
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a491c120dff7f8f505878d6887498eb5f05fb22
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792223"
---
# <a name="custom-c"></a>custom (C++)

Define los metadatos de un objeto en la biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>Parámetros

*uuid*<br/>
Identificador único.

*valor*<br/>
Un valor que se puede colocar en una variante.

## <a name="remarks"></a>Comentarios

El **personalizado** atributo de C++ hará que la información para colocarse en la biblioteca de tipos. Necesitará una herramienta que lee el valor personalizado de la biblioteca de tipos.

El **personalizado** atributo tiene la misma funcionalidad que el [personalizado](/windows/desktop/Midl/custom) atributo MIDL.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|No COM **interfaz**, **clase**, **enum**s, `idl_module` métodos, los miembros de interfaz, los parámetros de la interfaz, **typedef**s, **unión**s, **struct**s|
|**Reiterativo**|Sí|
|**Atributos requeridos**|**coclase** (cuando se usa en la clase)|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, vea [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)  