---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: f51b0210fff4db5be359fa94237f4d7c77b4fef2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214895"
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

*value*<br/>
Valor que se puede colocar en una variante.

## <a name="remarks"></a>Observaciones

El atributo **personalizado** C++ hará que la información se coloque en la biblioteca de tipos. Necesitará una herramienta que lea el valor personalizado de la biblioteca de tipos.

El atributo **personalizado** tiene la misma funcionalidad que el atributo MIDL [personalizado](/windows/win32/Midl/custom) .

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**Interfaz**no com, **clase**, **enumeración**, métodos de `idl_module`, miembros de interfaz, parámetros de interfaz, **typedef**s, **Union**s, **struct**s|
|**Reiterativo**|Sí|
|**Atributos requeridos**|**coclase** (cuando se usa en la clase)|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)
