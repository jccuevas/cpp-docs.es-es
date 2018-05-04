---
title: Macros de registro | Documentos de Microsoft
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
ms.openlocfilehash: ed9b172217f1ca7ada7d8752151126b53055df37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="registry-macros"></a>Macros de registro
Estas macros definen las instalaciones de biblioteca y el registro de un tipo útil.  
  
|||  
|-|-|  
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Indica que desea que el código de registro para el objeto en el objeto para evitar una dependencia de ATL. DLL.|  
|[DECLARE_LIBID](#declare_libid)|Proporciona una forma de ATL obtener la *libid* de la biblioteca de tipos.|  
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Evita el registro ATL de forma predeterminada.|  
|[DECLARE_REGISTRY](#declare_registry)|Escribe o quita la entrada del objeto principal en el registro del sistema.|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Especifica la información necesaria para registrar automáticamente el *appid*.|  
|[MACROS DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Busca el recurso con nombre y se ejecuta el script de registro dentro de él.|  
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Busca el recurso identificado por un número de identificación y ejecuta el script de registro dentro de él.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
    
##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY  
 Un símbolo que indica que desea que el código de registro para el objeto en el objeto para evitar una dependencia de ATL. DLL.  
  
```
#define _ATL_STATIC_REGISTRY
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando se define **ATL_STATIC_REGISTRY**, debe usar el código siguiente:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]  
  
##  <a name="declare_libid"></a>  DECLARE_LIBID  
 Proporciona una forma de ATL obtener la *libid* de la biblioteca de tipos.  
  
```
DECLARE_LIBID( libid )
```  
  
### <a name="parameters"></a>Parámetros  
 *LIBID*  
 El GUID de la biblioteca de tipos.  
  
### <a name="remarks"></a>Comentarios  
 Use `DECLARE_LIBID` en un `CAtlModuleT`-clase derivada.  
  
### <a name="example"></a>Ejemplo  
 El atributo no son generados por el asistente ATL (proyectos) tendrá un ejemplo del uso de esta macro.  
  
##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY  
 Use `DECLARE_NO_REGISTRY` si desea evitar cualquier registro ATL predeterminado para la clase en la que aparece esta macro.  
  
```
DECLARE_NO_REGISTRY()
```  
  
##  <a name="declare_registry"></a>  DECLARE_REGISTRY  
 Escribe el registro de la clase estándar en el registro del sistema o lo quita del registro del sistema.  
  
```
DECLARE_REGISTRY(
    class, 
    pid, 
    vpid, 
    nid, 
    flags )
```  
  
### <a name="parameters"></a>Parámetros  
 `class`  
 [in] Se incluye por compatibilidad con versiones anteriores.  
  
 `pid`  
 [in] Un `LPCTSTR` que es un identificador de programa específico de la versión.  
  
 *vpid*  
 [in] Un `LPCTSTR` que es un identificador de programa independiente de la versión.  
  
 *NID*  
 [in] A **UINT** que es un índice de la cadena de recurso en el registro que se usará como la descripción del programa.  
  
 `flags`  
 [in] Un `DWORD` que contiene el programa de subprocesamiento del modelo en el registro. Debe ser uno de los siguientes valores: **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, o **AUTPRXFLAG**.  
  
### <a name="remarks"></a>Comentarios  
 El registro estándar está formada por el CLSID, Id. de programa, Id. de programa independiente de la versión, cadena de descripción y el modelo de subprocesos.  
  
 Cuando se crea un objeto o controlar mediante el Asistente para agregar clases de ATL, el asistente implementa compatibilidad con el registro basado en script y agrega automáticamente el [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) macro en los archivos. Si no desea compatibilidad con el registro de secuencias de comandos, es necesario reemplazar esta macro con `DECLARE_REGISTRY`. `DECLARE_REGISTRY` Inserta únicamente las cinco teclas básicas que se ha descrito anteriormente en el registro. Debe escribir código para insertar otras claves en el registro manualmente.  
  
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
 Use `DECLARE_REGISTRY_APPID_RESOURCEID` en un `CAtlModuleT`-clase derivada.  
  
### <a name="example"></a>Ejemplo  
 Las clases que se agregará a los proyectos ATL con el Asistente de código Agregar clase tendrán un ejemplo del uso de esta macro.  
  
##  <a name="declare_registry_resource"></a>  MACROS DECLARE_REGISTRY_RESOURCE  
 Obtiene el recurso con nombre que contiene el archivo de registro y se ejecuta la secuencia de comandos para especificar objetos en el registro del sistema o quitarlos del registro del sistema.  
  
```
DECLARE_REGISTRY_RESOURCE( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] Identificador del recurso de cadena.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea un objeto o controlar mediante el Asistente para proyectos ATL, el asistente se implementan la compatibilidad de registro basado en script y agregar automáticamente el [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) (macro), que es similar a `DECLARE_REGISTRY_RESOURCE`, a su archivos.  
  
 Puede vincular estáticamente con el componente de registro de ATL (registrador) para acceder al registro optimizado. Para vincular estáticamente al código del registrador, agregue la siguiente línea al archivo stdafx.h:  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Si desea que ATL para sustituir valores de reemplazo en tiempo de ejecución, no especifique el `DECLARE_REGISTRY_RESOURCE` o `DECLARE_REGISTRY_RESOURCEID` macro. En su lugar, cree una matriz de **_ATL_REGMAP_ENTRIES** estructuras, donde cada entrada contiene un marcador de posición variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), pasar la matriz. Esto agrega todos los valores de reemplazo en el **_ATL_REGMAP_ENTRIES** estructuras al mapa de reemplazo del registrador.  

  
 Para obtener más información sobre los parámetros reemplazables y secuencias de comandos, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).  
  
##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID  
 Igual que [macros DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) salvo que usa un generados por el asistente **UINT** para identificar el recurso, en lugar de un nombre de cadena.  
  
```
DECLARE_REGISTRY_RESOURCEID( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] Identificador generado por el Asistente del recurso.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea un objeto o controlar mediante el Asistente para proyectos ATL, el asistente se implementan la compatibilidad de registro basado en script y agregar automáticamente el `DECLARE_REGISTRY_RESOURCEID` macro en los archivos.  
  
 Puede vincular estáticamente con el componente de registro de ATL (registrador) para acceder al registro optimizado. Para vincular estáticamente al código del registrador, agregue la siguiente línea al archivo stdafx.h:  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Si desea que ATL para sustituir valores de reemplazo en tiempo de ejecución, no especifique el `DECLARE_REGISTRY_RESOURCE` o `DECLARE_REGISTRY_RESOURCEID` macro. En su lugar, cree una matriz de **_ATL_REGMAP_ENTRIES** estructuras, donde cada entrada contiene un marcador de posición variable emparejado con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), pasar la matriz. Esto agrega todos los valores de reemplazo en el **_ATL_REGMAP_ENTRIES** estructuras al mapa de reemplazo del registrador.  

  
 Para obtener más información sobre los parámetros reemplazables y secuencias de comandos, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)
