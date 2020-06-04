---
title: uuid (Atributos de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: c507a9ae42afc5081c290d38464aa7f24c277d15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166125"
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

## <a name="remarks"></a>Observaciones

Si la definición de una interfaz o clase no especifica el atributo **UUID** C++ , el compilador C++ de Microsoft proporcionará uno. Al especificar un **UUID**, debe incluir las comillas.

Si no especifica **UUID**, el compilador generará el mismo GUID para las interfaces o clases con el mismo nombre en distintos proyectos de atributos de un equipo.

Puede usar Uuidgen. exe o Guidgen. exe para generar sus propios identificadores únicos. (Para ejecutar cualquiera de estas herramientas, haga clic en **Inicio** y en **Ejecutar** en el menú. A continuación, escriba el nombre de la herramienta necesaria).

Cuando se usa en un proyecto que no utiliza también ATL, la especificación del atributo **UUID** es la misma que la especificación del modificador **__declspec** [UUID](../../cpp/uuid-cpp.md) . Para recuperar el **UUID** de una clase, puede usar [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Ejemplo

Vea el ejemplo [enlazable](bindable.md) para obtener un ejemplo de uso de **UUID**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **estructura**, **interfaz**, **Unión**, **enumeración**|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)
