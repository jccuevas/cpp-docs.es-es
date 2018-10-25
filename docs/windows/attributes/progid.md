---
title: ProgID (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 239f50011c91320c2b5e0a96449139e8eeab10ff
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072869"
---
# <a name="progid"></a>progid

Especifica el ProgID de un objeto COM.

## <a name="syntax"></a>Sintaxis

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Parámetros

*name*<br/>
El ProgID que representa el objeto.

ProgID presentan una versión legible del identificador de clase (CLSID) usado para identificar los objetos COM y ActiveX.

## <a name="remarks"></a>Comentarios

El **progid** atributo de C++ le permite especificar el ProgID de un objeto COM. Un ProgID tiene la forma *name1.name2.version*. Si no especifica un *versión* para un ProgID, la versión predeterminada es 1. Si no especifica *name1.name2*, el nombre predeterminado es *classname.classname*. Si no especifica **progid** y especificar `vi_progid`, *name1.name2* se toman de `vi_progid` y el (siguiente número secuencial) se anexa la versión.

Si un bloque de atributos que usa **progid** no usa también **uuid**, el compilador comprobará si el registro para ver si un **uuid** existe para el elemento especificado **progid** . Si **progid** no se especifica, se usará la versión (y el nombre de coclase, si la creación de una coclase) para generar un **progid**.

**ProgID** implica la `coclass` atributo, es decir, si especifica **progid**, es lo mismo que si se especifica la `coclass` y **progid** atributos.

El **progid** atributo hace que una clase que se registren automáticamente con el nombre especificado. El archivo .idl generado no se mostrará el **progid** valor.

Cuando este atributo se utiliza dentro de un proyecto que usa ATL, cambia el comportamiento del atributo. Además del comportamiento anterior, la información especificada con este atributo se usa en el `GetProgID` función, insertado por el `coclass` atributo. Para obtener más información, consulte el [coclase](coclass.md) atributo.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [coclase](coclass.md) para un ejemplo de uso de **progid**.

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
[Atributos de clase](class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Clave de Id. de programa](/windows/desktop/com/-progid--key)
