---
title: Objeto Map Macros | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
dev_langs: C++
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 626744eb9f2d9dbe6a013bd329406150af35ecca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="object-map-macros"></a>Macros de mapa de objeto
Estas macros definen asignaciones de objeto y las entradas.  
  
|||  
|-|-|  
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Permite especificar la descripción de texto del objeto de clase, que se escribirá en el mapa de objetos.|  
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Escribe un objeto ATL en el mapa de objetos, actualiza el registro y crea una instancia del objeto.|  
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Le permite especificar que el objeto debe estar registrado e inicializado, pero no se debe poder crear externamente que se pueden crear con `CoCreateInstance`.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
   
##  <a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION  
 Permite especificar una descripción de texto para el objeto de clase.  
  
```
DECLARE_OBJECT_DESCRIPTION( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] Descripción del objeto de clase.  
  
### <a name="remarks"></a>Comentarios  
 ATL entra en esta descripción en el mapa de objetos a través de la [objeto OBJECT_ENTRY](http://msdn.microsoft.com/en-us/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd) macro.  
  
 `DECLARE_OBJECT_DESCRIPTION`implementa un `GetObjectDescription` función, que puede usar para invalidar la [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription) método.  

  
 El `GetObjectDescription` llama a función **IComponentRegistrar::GetComponents**. **IComponentRegistrar** es una interfaz de automatización que le permite registrar y anular el registro de componentes individuales en un archivo DLL. Cuando se crea un objeto de registrador de componentes con el Asistente para proyectos ATL, el Asistente implementará automáticamente el **IComponentRegistrar** interfaz. **IComponentRegistrar** se utiliza normalmente con Microsoft Transaction Server.  
  
 Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]  
  
##  <a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO  
 Escribe un objeto ATL en el mapa de objetos, actualiza el registro y crea una instancia del objeto.  
  
```
OBJECT_ENTRY_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 [in] El CLSID de una clase COM implementada por la clase de C++ denominada `class`.  
  
 `class`  
 [in] El nombre de la clase de C++ que implementa la clase COM representada por `clsid`.  
  
### <a name="remarks"></a>Comentarios  
 Las macros de entrada de objeto se colocan en el ámbito global del proyecto para proporcionar compatibilidad con el registro, la inicialización y la creación de una clase.  
  
 `OBJECT_ENTRY_AUTO`Escribe los punteros de función de la clase de creador y la clase del creador de generador de clases `CreateInstance` funciones para este objeto en el mapa de objetos ATL generado automáticamente. Cuando [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) es llama, actualiza el registro del sistema para cada objeto del mapa de objetos.  

  
 En la tabla siguiente describe cómo se obtiene la información que se agrega al mapa de objetos de la clase que se proporcionó como el segundo parámetro para esta macro.  
  
|Información de|Obtenido de|  
|---------------------|-------------------|  
|Registro de COM|[Macros de Registro](../../atl/reference/registry-macros.md)|  
|Creación del generador de clases|[Macros de fábrica de clase](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Creación de instancias|[Aggregation (Macros)](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Registro de la categoría de componente|[Macros de categoría](../../atl/reference/category-macros.md)|  
|La limpieza y la inicialización de nivel de clase|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

  
##  <a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO  
 Le permite especificar que el objeto debe estar registrado e inicializado, pero no se debe poder crear externamente que se pueden crear con `CoCreateInstance`.  
  
```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 [in] El CLSID de una clase COM implementada por la clase de C++ denominada `class`.  
  
 `class`  
 [in] El nombre de la clase de C++ que implementa la clase COM representada por `clsid`.  
  
### <a name="remarks"></a>Comentarios  
 Las macros de entrada de objeto se colocan en el ámbito global del proyecto para proporcionar compatibilidad con el registro, la inicialización y la creación de una clase.  
  
 `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO`le permite especificar que un objeto debe estar registrado e inicializado (vea [OBJECT_ENTRY_AUTO](#object_entry_auto) para obtener más información), pero no se debería crear con `CoCreateInstance`.  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)
