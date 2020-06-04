---
title: vi_progid (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: fbf5ab2bc4263356a1cfcf789865a3f7e286ccd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514861"
---
# <a name="vi_progid"></a>vi_progid

Especifica una forma independiente de la versión del identificador de programa (ProgID).

## <a name="syntax"></a>Sintaxis

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>Parámetros

*name*<br/>
ProgID independiente de la versión que representa el objeto.

Los ProgID presentan una versión legible del identificador de clase (CLSID) que se usa para identificar objetos COM/ActiveX.

## <a name="remarks"></a>Comentarios

El atributo **vi_progid** C++ permite especificar un ProgID independiente de la versión para un objeto com. Un ProgID tiene el formato *nombre1. nombre2. version*. Un ProgID independiente de la versión no tiene una *versión*. Es posible especificar los `progid` atributos y **vi_progid** en un. `coclass` Si no especifica **vi_progid**, el ProgID independiente de la versión es el valor especificado por el atributo [ProgID](progid.md) .

**vi_progid** implica el `coclass` atributo, es decir, si especifica **vi_progid**, es lo mismo que especificar los `coclass` atributos y **vi_progid** .

El atributo **vi_progid** hace que se registre automáticamente una clase en el nombre especificado. El archivo. idl generado no mostrará el valor de ProgID.

En los proyectos ATL, si el atributo [CoClass](coclass.md) también está presente, la `GetVersionIndependentProgID` función usa el ProgID especificado (insertado por el `coclass` atributo).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [coclase](coclass.md) para ver un ejemplo del uso de **vi_progid**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|Sin |
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Clave ProgID](/windows/win32/com/-progid--key)
