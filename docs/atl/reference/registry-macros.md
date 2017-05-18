---
title: Macros de registro | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 3a3abf5ad29b50c7f6708f02fd7c5aa193b3591c
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="registry-macros"></a>Macros de registro
Estas macros definen las instalaciones de biblioteca y el registro de tipo útil.  
  
|||  
|-|-|  
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Indica que desea que el código de registro para el objeto en el objeto de evitar la dependencia de ATL. DLL.|  
|[DECLARE_LIBID](#declare_libid)|Proporciona una forma de ATL obtener la *libid* de la biblioteca de tipos.|  
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Evita el registro de ATL de forma predeterminada.|  
|[DECLARE_REGISTRY](#declare_registry)|Entra o quita la entrada del objeto principal en el registro del sistema.|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Especifica la información necesaria para registrar automáticamente el *appid*.|  
|[MACROS DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Busca el recurso con nombre y se ejecuta la secuencia de comandos del registro dentro de él.|  
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Busca el recurso identificado por un número de identificador y se ejecuta la secuencia de comandos del registro dentro de él.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
    
##  <a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY  
 Un símbolo que indica que desea que el código de registro para el objeto en el objeto de evitar la dependencia de ATL. DLL.  
  
```
#define _ATL_STATIC_REGISTRY
```  
  
### <a name="remarks"></a>Comentarios  
 Al definir **ATL_STATIC_REGISTRY**, debe utilizar el siguiente código:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample&#5;](../../atl/codesnippet/cpp/registry-macros_1.cpp)]  
  
##  <a name="declare_libid"></a>DECLARE_LIBID  
 Proporciona una forma de ATL obtener la *libid* de la biblioteca de tipos.  
  
```
DECLARE_LIBID( libid )
```  
  
### <a name="parameters"></a>Parámetros  
 *LIBID*  
 El GUID de la biblioteca de tipos.  
  
### <a name="remarks"></a>Comentarios  
 Utilice `DECLARE_LIBID` en un `CAtlModuleT`-clase derivada.  
  
### <a name="example"></a>Ejemplo  
 Sin atributos generados por el Asistente para ATL (proyectos) tendrá un ejemplo del uso de esta macro.  
  
##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY  
 Use `DECLARE_NO_REGISTRY` si desea evitar cualquier registro ATL predeterminado para la clase en la que aparece esta macro.  
  
```
DECLARE_NO_REGISTRY()
```  
  
##  <a name="declare_registry"></a>DECLARE_REGISTRY  
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
 [in] Un `LPCTSTR` que es un identificador de programa específicos de la versión.  
  
 *vpid*  
 [in] Un `LPCTSTR` que es un identificador de programa independiente de la versión.  
  
 *NID*  
 [in] Un **UINT** que es un índice de la cadena de recurso en el registro como la descripción del programa.  
  
 `flags`  
 [in] Un `DWORD` que contiene el programa de subprocesos del modelo en el registro. Debe ser uno de los siguientes valores: **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, o **AUTPRXFLAG**.  
  
### <a name="remarks"></a>Comentarios  
 El registro estándar está formada por el CLSID, Id. de programa, Id. de programa independiente de la versión, cadena de descripción y el modelo de subprocesos.  
  
 Cuando se crea un objeto o controlar mediante el Asistente para agregar clases de ATL, el asistente implementa la compatibilidad con secuencias de comandos de registro y agrega automáticamente el [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) macro en los archivos. Si no desea compatibilidad con el registro de secuencias de comandos, debe reemplazar esta macro con `DECLARE_REGISTRY`. `DECLARE_REGISTRY`sólo inserta las cinco claves básicas descritas anteriormente en el registro. Debe escribir código para insertar otras claves del registro manualmente.  
  
##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID  
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
 Utilice `DECLARE_REGISTRY_APPID_RESOURCEID` en un `CAtlModuleT`-clase derivada.  
  
### <a name="example"></a>Ejemplo  
 Clases agregadas a proyectos ATL con el Asistente de código Agregar clase tendrá un ejemplo del uso de esta macro.  
  
##  <a name="declare_registry_resource"></a>MACROS DECLARE_REGISTRY_RESOURCE  
 Obtiene el recurso con nombre que contiene el archivo de registro y se ejecuta la secuencia de comandos para escribir objetos en el registro del sistema o quitarlas del registro del sistema.  
  
```
DECLARE_REGISTRY_RESOURCE( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] Identificador del recurso de cadena.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea un objeto o controlar mediante el Asistente para proyectos ATL, el asistente automáticamente implementar la compatibilidad con secuencias de comandos de registro y agregar la [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) (macro), que es similar a `DECLARE_REGISTRY_RESOURCE`, a los archivos.  
  
 Puede vincular estáticamente con el componente de registro de ATL (registrador) para acceder al registro optimizado. Para vincular estáticamente al código del registrador, agregue la siguiente línea al archivo stdafx.h:  
  
 [!code-cpp[NVC_ATL_COM Nº&56;](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Si desea que ATL para sustituir valores de reemplazo en tiempo de ejecución, no especifique el `DECLARE_REGISTRY_RESOURCE` o `DECLARE_REGISTRY_RESOURCEID` (macro). En su lugar, cree una matriz de **_ATL_REGMAP_ENTRIES** estructuras, donde cada entrada contiene un marcador de posición variable emparejan con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), pasando la matriz. Esto agrega todos los valores de reemplazo en el **_ATL_REGMAP_ENTRIES** estructuras al mapa de reemplazo del registrador.  

  
 Para obtener más información acerca de los parámetros reemplazables y secuencias de comandos, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).  
  
##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID  
 Igual que [macros DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) salvo que usa un asistente generó **UINT** para identificar el recurso, en lugar de un nombre de cadena.  
  
```
DECLARE_REGISTRY_RESOURCEID( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] Identificador generado por el Asistente del recurso.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea un objeto o controlar mediante el Asistente para proyectos ATL, el asistente automáticamente implementar la compatibilidad con secuencias de comandos de registro y agregar la `DECLARE_REGISTRY_RESOURCEID` macro en los archivos.  
  
 Puede vincular estáticamente con el componente de registro de ATL (registrador) para acceder al registro optimizado. Para vincular estáticamente al código del registrador, agregue la siguiente línea al archivo stdafx.h:  
  
 [!code-cpp[NVC_ATL_COM Nº&56;](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Si desea que ATL para sustituir valores de reemplazo en tiempo de ejecución, no especifique el `DECLARE_REGISTRY_RESOURCE` o `DECLARE_REGISTRY_RESOURCEID` (macro). En su lugar, cree una matriz de **_ATL_REGMAP_ENTRIES** estructuras, donde cada entrada contiene un marcador de posición variable emparejan con un valor para reemplazar el marcador de posición en tiempo de ejecución. A continuación, llame a [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), pasando la matriz. Esto agrega todos los valores de reemplazo en el **_ATL_REGMAP_ENTRIES** estructuras al mapa de reemplazo del registrador.  

  
 Para obtener más información acerca de los parámetros reemplazables y secuencias de comandos, vea el artículo [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)

