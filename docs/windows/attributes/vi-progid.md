---
title: vi_progid (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: 7050543c9acf3801a99d3e32e119325900bdb050
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033594"
---
# <a name="viprogid"></a>vi_progid

Especifica una forma independiente de la versión de ProgID.

## <a name="syntax"></a>Sintaxis

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>Parámetros

*name*<br/>
El ProgID independientes de la versión que representa el objeto.

ProgID presentan una versión legible del identificador de clase (CLSID) usado para identificar los objetos COM y ActiveX.

## <a name="remarks"></a>Comentarios

El **vi_progid** atributo de C++ le permite especificar un ProgID independientes de la versión de un objeto COM. Un ProgID tiene la forma *name1.name2.version*. Un ProgID independientes de la versión no tiene un *versión*. Es posible especificar ambos el `progid` y **vi_progid** atributos en un `coclass`. Si no especifica **vi_progid**, el ProgID independientes de la versión es el valor especificado por el [progid](progid.md) atributo.

**vi_progid** implica la `coclass` atributo, es decir, si especifica **vi_progid**, es lo mismo que si se especifica la `coclass` y **vi_progid** atributos.

El **vi_progid** atributo hace que una clase que se registren automáticamente con el nombre especificado. El archivo .idl generado no mostrará el valor de Id. de programa.

En los proyectos ATL, si la [coclase](coclass.md) atributo también está presente, se utiliza el ProgID especificado por el `GetVersionIndependentProgID` función (insertada por el `coclass` atributo).

## <a name="example"></a>Ejemplo

Consulte la [coclase](coclass.md) ejemplo para un ejemplo de uso de **vi_progid**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (Atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[ProgID Key](/windows/desktop/com/-progid--key)
