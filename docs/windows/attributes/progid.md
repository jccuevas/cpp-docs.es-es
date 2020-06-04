---
title: ProgID (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: d529d7362dc62207cfd72576159f560a3e04c221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514249"
---
# <a name="progid"></a>progid

Especifica el ProgID para un objeto COM.

## <a name="syntax"></a>Sintaxis

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Parámetros

*name*<br/>
Identificador de programa (ProgID) que representa el objeto.

Los ProgID presentan una versión legible del identificador de clase (CLSID) que se usa para identificar objetos COM/ActiveX.

## <a name="remarks"></a>Comentarios

El atributo **ProgID** C++ permite especificar el identificador de programa (ProgID) de un objeto com. Un ProgID tiene el formato *nombre1. nombre2. version*. Si no especifica una *versión* para un ProgID, la versión predeterminada es 1. Si no especifica *nombre1. nombre2*, el nombre predeterminado es *className. ClassName*. Si no especifica **ProgID** y especifica `vi_progid`, *nombre1. nombre2* se toma de `vi_progid` y se anexa la versión (siguiente número secuencial).

Si un bloque de atributos que utiliza **ProgID** no usa también el **UUID**, el compilador comprobará el registro para ver si existe un **UUID** para el **ProgID**especificado. Si no se especifica **ProgID** , la versión (y el nombre de coclase, si se crea una coclase) se usarán para generar un **ProgID**.

**ProgID** implica el `coclass` atributo, es decir, si especifica **ProgID**, es lo mismo que especificar los `coclass` atributos y **ProgID** .

El atributo **ProgID** hace que una clase se registre automáticamente en el nombre especificado. El archivo. idl generado no mostrará el valor de **ProgID** .

Cuando este atributo se usa en un proyecto que usa ATL, el comportamiento del atributo cambia. Además del comportamiento anterior, la información especificada con este atributo se usa en la `GetProgID` función, insertada por el `coclass` atributo. Para obtener más información, vea el atributo [CoClass](coclass.md) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [coclase](coclass.md) para obtener un ejemplo del uso de **ProgID**.

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
[Atributos de clase](class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Clave ProgID](/windows/win32/com/-progid--key)
