---
title: Macros de registro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56be1e0b5490aa6b6e97b578a7bbf90bcdcca7c8
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880974"
---
# <a name="registry-macros"></a>Macros de registro
Estas macros definen las instalaciones de biblioteca y el registro de tipo útil.  
  
|||  
|-|-|  
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Indica que desea que el código de registro para el objeto en el objeto para evitar una dependencia en ATL. ARCHIVO DLL.|  
|[DECLARE_LIBID](#declare_libid)|Proporciona una manera de ATL obtener el *libid* de la biblioteca de tipos.|  
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Evita el registro de ATL de forma predeterminada.|  
|[DECLARE_REGISTRY](#declare_registry)|Escribe o quita la entrada del objeto principal en el registro del sistema.|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Especifica la información necesaria para registrar automáticamente el *appid*.|  
|[MACROS DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Busca el recurso con nombre y se ejecuta el script del registro dentro de él.|  
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Busca el recurso identificado por un número de identificación y se ejecuta el script del registro dentro de él.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
    
##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY  
 Un símbolo que indica que desea que el código de registro para el objeto en el objeto para evitar una dependencia en ATL. ARCHIVO DLL.  
  
```
#define _ATL_STATIC_REGISTRY
```  
  
### <a name="remarks"></a>Comentarios  
 Al definir ATL_STATIC_REGISTRY, debe usar el código siguiente:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]  
  
##  <a name="declare_libid"></a>  DECLARE_LIBID  
 Proporciona una manera de ATL obtener el *libid* de la biblioteca de tipos.  
  
```
DECLARE_LIBID( libid )
```  
  
### <a name="parameters"></a>Parámetros  
 *LIBID*  
 El GUID de la biblioteca de tipos.  
  
### <a name="remarks"></a>Comentarios  
 Usar DECLARE_LIBID en un `CAtlModuleT`-clase derivada.  
  
### <a name="example"></a>Ejemplo  
 Sin atributos generados por el Asistente para proyectos ATL tendrá un ejemplo del uso de esta macro.  
  
##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY  
 Si desea evitar cualquier registro ATL predeterminado para la clase en la que aparece esta macro, utilice DECLARE_NO_REGISTRY.  
  
```
DECLARE_NO_REGISTRY()
```  
  
##  <a name="declare_registry"></a>  DECLARE_REGISTRY  
 Escribe el registro de clase estándar en el registro del sistema o lo quita del registro del sistema.  
  
```
DECLARE_REGISTRY(
    class, 
    pid, 
    vpid, 
    nid, 
    flags )
```  
  
### <a name="parameters"></a>Parámetros  
 *class*  
 [in] Se incluye por compatibilidad con versiones anteriores.  
  
 *pid*  
 [in] LPCTSTR que es un identificador de programa específico de la versión.  
  
 *vpid*  
 [in] LPCTSTR que es un identificador de programa independiente de la versión.  
  
 *NID*  
 [in] Un tipo UINT que es un índice de la cadena de recurso en el registro que se usará como la descripción del programa.  
  
 *flags*  
 [in] DWORD que contiene el modelo de subprocesos del programa en el registro. Debe ser uno de los siguientes valores: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH o AUTPRXFLAG.  
  
### <a name="remarks"></a>Comentarios  
 El registro estándar consta de los CLSID, Id. de programa, Id. de programa independiente de la versión, cadena de descripción y el modelo de subprocesos.  
  
 Cuando se crea un objeto o controlar mediante el Asistente para agregar clases de ATL, el asistente implementa la compatibilidad con secuencias de comandos del registro automáticamente y agrega el [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) macro a los archivos. Si no desea compatibilidad con el registro basado en script, deberá reemplazar esta macro con DECLARE_REGISTRY. DECLARE_REGISTRY sólo inserta las cinco claves básicas que se ha descrito anteriormente en el registro. Debe escribir código para insertar otras claves en el registro manualmente.  
  
##  <a name="declare_registry_appid_resourceid"></a>  DECLARE_REGISTRY_APPID_RESOURCEID  
 Especifica la información necesaria para registrar automáticamente el *appid*.  
  
```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid, 
    appid )
```  
  
### <a name="parameters"></a>Parámetros  
 *RESID*  
 El identificador de recurso del archivo .rgs que contiene información sobre la *appid*.  
  
 *AppID*  
 Un GUID.  
  
### <a name="remarks"></a>Comentarios  
 Usar DECLARE_REGISTRY_APPID_RESOURCEID en un `CAtlModuleT`-clase derivada.  
  
### <a name="example"></a>Ejemplo  
 Las clases agregadas a proyectos ATL con el Asistente de código Agregar clase tendrá un ejemplo del uso de esta macro.  
  
##  <a name="declare_registry_resource"></a>  MACROS DECLARE_REGISTRY_RESOURCE  
 Obtiene el recurso con nombre que contiene el archivo de registro y se ejecuta la secuencia de comandos para especificar los objetos en el registro del sistema o quitarlas del registro del sistema.  
  
```
DECLARE_REGISTRY_RESOURCE( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] Identificador del recurso de cadena.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea un objeto o controlar mediante el Asistente para proyectos ATL, el asistente automáticamente implementar la compatibilidad con secuencias de comandos del registro y agregue el [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) macro, que es similar a DECLARE_REGISTRY_ RECURSOS a los archivos.  
  
 Puede vincular estáticamente con el componente de registro de ATL (registrador) para acceder al registro optimizado. Para vincular estáticamente al código del registrador, agregue la siguiente línea al archivo stdafx.h:  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Si desea que ATL para sustituir los valores de reemplazo en tiempo de ejecución, no especifique la macro macros DECLARE_REGISTRY_RESOURCE o DECLARE_REGISTRY_RESOURCEID. En su lugar, cree una matriz de `_ATL_REGMAP_ENTRIES` estructuras, donde cada entrada contiene un marcador de posición variable emparejan con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), pasando la matriz. Esto agrega todos los valores de reemplazo en el `_ATL_REGMAP_ENTRIES` estructuras al mapa de reemplazo del registrador.  

  
 Para obtener más información acerca de los parámetros reemplazables y secuencias de comandos, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).  
  
##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID  
 Igual que [macros DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) salvo que usa un tipo UINT generados por el Asistente para identificar el recurso, en lugar de un nombre de cadena.  
  
```
DECLARE_REGISTRY_RESOURCEID( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] Identificador generado por el Asistente del recurso.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea un objeto o un control mediante el Asistente para proyectos ATL, el asistente automáticamente implementar la compatibilidad con secuencias de comandos del registro y agregar la macro DECLARE_REGISTRY_RESOURCEID a los archivos.  
  
 Puede vincular estáticamente con el componente de registro de ATL (registrador) para acceder al registro optimizado. Para vincular estáticamente al código del registrador, agregue la siguiente línea al archivo stdafx.h:  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Si desea que ATL para sustituir los valores de reemplazo en tiempo de ejecución, no especifique la macro macros DECLARE_REGISTRY_RESOURCE o DECLARE_REGISTRY_RESOURCEID. En su lugar, cree una matriz de `_ATL_REGMAP_ENTRIES` estructuras, donde cada entrada contiene un marcador de posición variable emparejan con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), pasando la matriz. Esto agrega todos los valores de reemplazo en el `_ATL_REGMAP_ENTRIES` estructuras al mapa de reemplazo del registrador.  

  
 Para obtener más información acerca de los parámetros reemplazables y secuencias de comandos, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)
