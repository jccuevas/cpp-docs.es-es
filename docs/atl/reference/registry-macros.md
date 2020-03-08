---
title: Macros de registro
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
ms.openlocfilehash: c2a70c15473798ba6eb2ef35e0b7ded395708586
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857160"
---
# <a name="registry-macros"></a>Macros de registro

Estas macros definen funciones de registro y biblioteca de tipos útiles.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Indica que desea que el código de registro del objeto esté en el objeto para evitar una dependencia en ATL. DLL.|
|[DECLARE_LIBID](#declare_libid)|Proporciona una manera para que ATL obtenga el *Libid* de la biblioteca de tipos.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Evita el registro ATL predeterminado.|
|[DECLARE_REGISTRY](#declare_registry)|Especifica o quita la entrada del objeto principal en el registro del sistema.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Especifica la información necesaria para registrar automáticamente el *AppID*.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Busca el recurso con nombre y ejecuta el script del registro en él.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Busca el recurso identificado por un número de identificación y ejecuta el script del registro en él.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

Símbolo que indica que se desea que el código de registro del objeto esté en el objeto para evitar una dependencia en ATL. DLL.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Observaciones

Al definir ATL_STATIC_REGISTRY, debe usar el código siguiente:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>DECLARE_LIBID

Proporciona una manera para que ATL obtenga el *Libid* de la biblioteca de tipos.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Parámetros

*Libid*<br/>
GUID de la biblioteca de tipos.

### <a name="remarks"></a>Observaciones

Utilice DECLARE_LIBID en una clase derivada de `CAtlModuleT`.

### <a name="example"></a>Ejemplo

Los proyectos ATL no con atributos generados por el asistente tendrán un ejemplo de uso de esta macro.

##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

Use DECLARE_NO_REGISTRY si desea evitar el registro ATL predeterminado para la clase en la que aparece esta macro.

```
DECLARE_NO_REGISTRY()
```

##  <a name="declare_registry"></a>DECLARE_REGISTRY

Especifica el registro de la clase estándar en el registro del sistema o lo quita del registro del sistema.

```
DECLARE_REGISTRY(
    class,
    pid,
    vpid,
    nid,
    flags )
```

### <a name="parameters"></a>Parámetros

*class*<br/>
de Se incluye para la compatibilidad con versiones anteriores.

*pid*<br/>
de Un LPCTSTR que es un identificador de programa específico de la versión.

*vpid*<br/>
de Un LPCTSTR que es un identificador de programa independiente de la versión.

*Nid*<br/>
de Un valor UINT que es un índice de la cadena de recursos del registro que se va a utilizar como Descripción del programa.

*flags*<br/>
de DWORD que contiene el modelo de subprocesos del programa en el registro. Debe ser uno de los siguientes valores: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH o AUTPRXFLAG.

### <a name="remarks"></a>Observaciones

El registro estándar consta de CLSID, identificador de programa, identificador de programa independiente de la versión, cadena de Descripción y modelo de subproceso.

Al crear un objeto o un control mediante el Asistente para agregar clases ATL, el asistente implementa automáticamente la compatibilidad con el registro basado en script y agrega la macro [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) a los archivos. Si no desea admitir registros basados en scripts, debe reemplazar esta macro por DECLARE_REGISTRY. DECLARE_REGISTRY solo inserta las cinco claves básicas descritas anteriormente en el registro. Debe escribir código manualmente para insertar otras claves en el registro.

##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

Especifica la información necesaria para registrar automáticamente el *AppID*.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Parámetros

*Resid*<br/>
Identificador de recurso del archivo. RGS que contiene información sobre el *AppID*.

*AppID*<br/>
Un GUID.

### <a name="remarks"></a>Observaciones

Utilice DECLARE_REGISTRY_APPID_RESOURCEID en una clase derivada de `CAtlModuleT`.

### <a name="example"></a>Ejemplo

Las clases agregadas a proyectos ATL con el Asistente para agregar código de clase tendrán un ejemplo de uso de esta macro.

##  <a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

Obtiene el recurso con nombre que contiene el archivo de registro y ejecuta el script para escribir objetos en el registro del sistema o quitarlos del registro del sistema.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Identificador de cadena del recurso.

### <a name="remarks"></a>Observaciones

Al crear un objeto o un control mediante el Asistente para proyectos ATL, el asistente implementará automáticamente la compatibilidad con el registro basada en script y agregará la macro [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) , que es similar a DECLARE_REGISTRY_RESOURCE, a los archivos.

Puede vincular estáticamente con el componente de registro de ATL (registrador) para obtener acceso al registro optimizado. Para vincular estáticamente al código del registrador, agregue la siguiente línea al archivo *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Si desea que ATL sustituya los valores de reemplazo en tiempo de ejecución, no especifique el DECLARE_REGISTRY_RESOURCE ni la macro DECLARE_REGISTRY_RESOURCEID. En su lugar, cree una matriz de estructuras `_ATL_REGMAP_ENTRIES`, donde cada entrada contiene un marcador de posición de variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), pasando la matriz. Así se agregan todos los valores de reemplazo de las estructuras `_ATL_REGMAP_ENTRIES` a la asignación de reemplazo del registrador.

Para obtener más información sobre los parámetros reemplazables y los scripts, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).

##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

Igual que [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) , salvo que usa un valor uint generado por el Asistente para identificar el recurso, en lugar de un nombre de cadena.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Identificador generado por el asistente del recurso.

### <a name="remarks"></a>Observaciones

Al crear un objeto o un control mediante el Asistente para proyectos ATL, el asistente implementará automáticamente la compatibilidad con el registro basada en script y agregará la macro DECLARE_REGISTRY_RESOURCEID a los archivos.

Puede vincular estáticamente con el componente de registro de ATL (registrador) para obtener acceso al registro optimizado. Para vincular estáticamente al código del registrador, agregue la siguiente línea al archivo *stdafx. h* (*PCH. h* en Visual Studio 2019 y versiones posteriores):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Si desea que ATL sustituya los valores de reemplazo en tiempo de ejecución, no especifique el DECLARE_REGISTRY_RESOURCE ni la macro DECLARE_REGISTRY_RESOURCEID. En su lugar, cree una matriz de estructuras `_ATL_REGMAP_ENTRIES`, donde cada entrada contiene un marcador de posición de variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), pasando la matriz. Así se agregan todos los valores de reemplazo de las estructuras `_ATL_REGMAP_ENTRIES` a la asignación de reemplazo del registrador.

Para obtener más información sobre los parámetros reemplazables y los scripts, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
