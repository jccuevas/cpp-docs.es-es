---
title: uuid (Atributos de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: d644f59ac92bf4e39f191c291dd4fef626411c3d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514951"
---
# <a name="uuid-c-attributes"></a>uuid (Atributos de C++)

Especifica el identificador único de una clase o interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>Parámetros

*uuid*<br/>
Identificador único de 128 bits.

## <a name="remarks"></a>Comentarios

Si la definición de una interfaz o clase no especifica el atributo **UUID** C++ , el compilador C++ de Microsoft proporcionará uno. Al especificar un **UUID**, debe incluir las comillas.

Si no especifica **UUID**, el compilador generará el mismo GUID para las interfaces o clases con el mismo nombre en distintos proyectos de atributos de un equipo.

Puede usar Uuidgen. exe o Guidgen. exe para generar sus propios identificadores únicos. (Para ejecutar cualquiera de estas herramientas, haga clic en **Inicio** y en **Ejecutar** en el menú. A continuación, escriba el nombre de la herramienta necesaria).

Cuando se usa en un proyecto que no utiliza también ATL, especificar el atributo **UUID** es el mismo que si se especifica el modificador [UUID](../../cpp/uuid-cpp.md) **_ _ declspec** . Para recuperar el **UUID** de una clase, puede usar _ _ [uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Ejemplo

Vea el ejemplo [enlazable](bindable.md) para obtener un ejemplo de uso de **UUID**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **estructura**, **interfaz**, **Unión**, **enumeración**|
|**Reiterativo**|Sin |
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)