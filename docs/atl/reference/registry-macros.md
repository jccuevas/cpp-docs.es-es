---
title: Macros del Registro
ms.date: 08/19/2019
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
ms.openlocfilehash: fd012b4300f4cd72cdc9ab363b770ac1dbefa06e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326039"
---
# <a name="registry-macros"></a>Macros del Registro

Estas macros definen instalaciones útiles de biblioteca de tipos y del registro.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Indica que desea que el código de registro del objeto esté en el objeto para evitar una dependencia de ATL. Dll.|
|[DECLARE_LIBID](#declare_libid)|Proporciona una manera para que ATL obtenga el *libid* de la biblioteca de tipos.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Evita el registro ATL predeterminado.|
|[DECLARE_REGISTRY](#declare_registry)|Introduce o quita la entrada del objeto principal en el registro del sistema.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Especifica la información necesaria para registrar automáticamente el *appid*.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Busca el recurso con nombre y ejecuta el script del Registro dentro de él.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Busca el recurso identificado por un número de IDENTIFICADOR y ejecuta el script del Registro dentro de él.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="_atl_static_registry"></a><a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

Símbolo que indica que desea que el código de registro del objeto esté en el objeto para evitar una dependencia de ATL. Dll.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Observaciones

Al definir ATL_STATIC_REGISTRY, debe utilizar el código siguiente:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

## <a name="declare_libid"></a><a name="declare_libid"></a>DECLARE_LIBID

Proporciona una manera para que ATL obtenga el *libid* de la biblioteca de tipos.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Parámetros

*libid*<br/>
GUID de la biblioteca de tipos.

### <a name="remarks"></a>Observaciones

Utilice DECLARE_LIBID `CAtlModuleT`en una clase derivada.

### <a name="example"></a>Ejemplo

Los proyectos ATL generados por asistentes no atribuidos tendrán un ejemplo del uso de esta macro.

## <a name="declare_no_registry"></a><a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

Utilice DECLARE_NO_REGISTRY si desea evitar cualquier registro ATL predeterminado para la clase en la que aparece esta macro.

```
DECLARE_NO_REGISTRY()
```

## <a name="declare_registry"></a><a name="declare_registry"></a>DECLARE_REGISTRY

Introduce el registro de clase estándar en el registro del sistema o lo elimina del registro del sistema.

```
DECLARE_REGISTRY(
    class,
    pid,
    vpid,
    nid,
    flags )
```

### <a name="parameters"></a>Parámetros

*clase*<br/>
[en] Incluido para compatibilidad con versiones anteriores.

*Pid*<br/>
[en] Un LPCTSTR que es un identificador de programa específico de la versión.

*vpid*<br/>
[en] Un LPCTSTR que es un identificador de programa independiente de la versión.

*Nid*<br/>
[en] UINT que es un índice de la cadena de recursos en el registro que se usará como descripción del programa.

*Banderas*<br/>
[en] DWORD que contiene el modelo de subprocesos del programa en el registro. Debe ser uno de los siguientes valores: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH o AUTPRXFLAG.

### <a name="remarks"></a>Observaciones

El registro estándar consta de CLSID, ID de programa, ID de programa independiente de la versión, cadena de descripción y modelo de subproceso.

Al crear un objeto o control mediante el Asistente para agregar clases ATL, el asistente implementa automáticamente la compatibilidad con el registro basada en scripts y agrega la macro [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) a los archivos. Si no desea compatibilidad con el registro basado en scripts, debe reemplazar esta macro con DECLARE_REGISTRY. DECLARE_REGISTRY solo inserta las cinco claves básicas descritas anteriormente en el registro. Debe escribir manualmente código para insertar otras claves en el registro.

## <a name="declare_registry_appid_resourceid"></a><a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

Especifica la información necesaria para registrar automáticamente el *appid*.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Parámetros

*Resnum*<br/>
El identificador de recurso del archivo .rgs que contiene información sobre el *appid*.

*Appid*<br/>
Un GUID.

### <a name="remarks"></a>Observaciones

Utilice DECLARE_REGISTRY_APPID_RESOURCEID `CAtlModuleT`en una clase derivada.

### <a name="example"></a>Ejemplo

Las clases agregadas a proyectos ATL con el Asistente para agregar código de clase tendrán un ejemplo de uso de esta macro.

## <a name="declare_registry_resource"></a><a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

Obtiene el recurso con nombre que contiene el archivo de registro y ejecuta el script para introducir objetos en el registro del sistema o quitarlos del registro del sistema.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] Identificador de cadena del recurso.

### <a name="remarks"></a>Observaciones

Al crear un objeto o control mediante el Asistente para proyectos ATL, el asistente implementará automáticamente la compatibilidad del Registro basada en scripts y agregará la macro [DECLARE_REGISTRY_RESOURCEID,](#declare_registry_resourceid) que es similar a DECLARE_REGISTRY_RESOURCE, a los archivos.

Puede vincular estáticamente con el componente de registro ATL (Registrar) para optimizar el acceso al registro. Para vincular estáticamente al código del registrador, agregue la siguiente línea al archivo *pch.h* (*stdafx.h* en Visual Studio 2017 y versiones anteriores):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Si desea que ATL sustituya los valores de sustitución en tiempo de ejecución, no especifique la macro DECLARE_REGISTRY_RESOURCE o DECLARE_REGISTRY_RESOURCEID. En su lugar, `_ATL_REGMAP_ENTRIES` cree una matriz de estructuras, donde cada entrada contiene un marcador de posición variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), pasando la matriz. Esto agrega todos los valores `_ATL_REGMAP_ENTRIES` de reemplazo en las estructuras al mapa de reemplazo del registrador.

Para obtener más información acerca de los parámetros reemplazables y el scripting, consulte el artículo [Componente del Registro ATL (Registrar).](../../atl/atl-registry-component-registrar.md)

## <a name="declare_registry_resourceid"></a><a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

Igual que [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) excepto que usa un UINT generado por el asistente para identificar el recurso, en lugar de un nombre de cadena.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] Identificador generado por el asistente del recurso.

### <a name="remarks"></a>Observaciones

Al crear un objeto o control mediante el Asistente para proyectos ATL, el asistente implementará automáticamente la compatibilidad del Registro basada en scripts y agregará la macro DECLARE_REGISTRY_RESOURCEID a los archivos.

Puede vincular estáticamente con el componente de registro ATL (Registrar) para optimizar el acceso al registro. Para vincular estáticamente al código del registrador, agregue la siguiente línea al archivo *stdafx.h* (*pch.h* en Visual Studio 2019 y versiones posteriores):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Si desea que ATL sustituya los valores de sustitución en tiempo de ejecución, no especifique la macro DECLARE_REGISTRY_RESOURCE o DECLARE_REGISTRY_RESOURCEID. En su lugar, `_ATL_REGMAP_ENTRIES` cree una matriz de estructuras, donde cada entrada contiene un marcador de posición variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), pasando la matriz. Esto agrega todos los valores `_ATL_REGMAP_ENTRIES` de reemplazo en las estructuras al mapa de reemplazo del registrador.

Para obtener más información acerca de los parámetros reemplazables y el scripting, consulte el artículo [Componente del Registro ATL (Registrar).](../../atl/atl-registry-component-registrar.md)

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
