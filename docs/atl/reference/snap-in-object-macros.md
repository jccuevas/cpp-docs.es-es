---
title: Macros de objeto del complemento | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
dev_langs: C++
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b70a8e3d644389bcfb21b276c5a3bcfad84891a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="snap-in-object-macros"></a>Macros de objeto del complemento
Estas macros proporcionan compatibilidad para extensiones de complemento.  
  
|||  
|-|-|  
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Marca el principio de la asignación de clase de datos de extensión de complemento para un objeto de complemento.|  
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Marca el principio de la asignación de la barra de herramientas para un objeto de complemento.|  
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Marca el final de la asignación de clase de datos de extensión de complemento de un objeto de complemento.|  
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Marca el final de la asignación de la barra de herramientas para un objeto de complemento.|  
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Crea a un miembro de datos para la clase de datos de la extensión de complemento.|  
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Escribe una clase de datos de extensión de complemento en la asignación de clase de datos de extensión de complemento del objeto de complemento.|  
|[SNAPINMENUID](#snapinmenuid)|Declara el identificador del menú contextual usado por el objeto de complemento.|  
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Escribe una barra de herramientas en el mapa de barra de herramientas del complemento de objeto.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsnap.h 
   
##  <a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP  
 Marca el principio de la asignación de clase de datos de extensión de complemento.  
  
```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```  
  
### <a name="parameters"></a>Parámetros  
 *classname*  
 [in] El nombre de la clase de datos de extensión de complemento.  
  
### <a name="remarks"></a>Comentarios  
 Iniciar la asignación de extensión de complemento con el `BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP` macro, agregue entradas para cada uno de los tipos de datos de extensión de complemento con el [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) (macro) y complete el mapa con la [END_ EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) macro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP  
 Declara el principio de la asignación de Id. de la barra de herramientas para el objeto de complemento.  
  
```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```  
  
### <a name="parameters"></a>Parámetros  
 `_class`  
 [in] Especifica la clase de objeto de complemento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]  
  
##  <a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP  
 Marca el final de la asignación de clase de datos de extensión de complemento.  
  
```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```  
  
### <a name="remarks"></a>Comentarios  
 Iniciar la asignación de extensión de complemento con el [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) macro, agregar entradas para cada uno de los tipos de datos del complemento de extensión con el [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) (macro), y complete el mapa con la `END_EXTENSION_SNAPIN_NODEINFO_MAP` macro.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).  
  
##  <a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP  
 Declara el final de la asignación de Id. de barra de herramientas para el objeto de complemento.  
  
```
END_SNAPINTOOLBARID_MAP( _class )
```  
  
### <a name="parameters"></a>Parámetros  
 `_class`  
 [in] Especifica la clase de objeto de complemento.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).  
  
##  <a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS  
 Agrega un miembro de datos a la clase de datos de extensión de complemento para una **ISnapInItemImpl**-clase derivada.  
  
```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```  
  
### <a name="parameters"></a>Parámetros  
 `dataClass`  
 [in] La clase de datos de la extensión de complemento.  
  
### <a name="remarks"></a>Comentarios  
 Esta clase también debe especificarse en una asignación de clase de datos de extensión de complemento. Iniciar la asignación de clase de datos de extensión de complemento con el [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) macros, agregue entradas para cada uno de los tipos de datos de extensión de complemento con el [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)(macro) y complete el mapa con la [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) macro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY  
 Agrega una clase de datos de extensión de complemento a la asignación de clase de datos de extensión de complemento.  
  
```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```  
  
### <a name="parameters"></a>Parámetros  
 `dataClass`  
 [in] La clase de datos de la extensión de complemento.  
  
### <a name="remarks"></a>Comentarios  
 Iniciar la asignación de clase de datos de extensión de complemento con el [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) macros, agregue entradas para cada uno de los tipos de datos de extensión de complemento con el `EXTENSION_SNAPIN_NODEINFO_ENTRY` macro y complete el mapa con la [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) macro.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).  
  
##  <a name="snapinmenuid"></a>SNAPINMENUID  
 Use esta macro para declarar el recurso de menú de contexto del objeto de complemento.  
  
```
SNAPINMENUID( id )
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] Identifica el menú contextual del objeto de complemento.  
  
##  <a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY  
 Use esta macro para especificar un identificador de la barra de herramientas en el complemento de barra de herramientas Id. de asignación de objetos.  
  
```
SNAPINTOOLBARID_ENTRY( id )
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] Identifica el control de barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 El [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) macro marca el principio de la asignación de Id. de la barra de herramientas; el [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) macro marca el final.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)
