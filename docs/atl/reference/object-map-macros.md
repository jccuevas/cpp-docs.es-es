---
title: Macros de mapa de objeto | Documentos de Microsoft
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
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: f03ca61c6ab3c550c316b380d34eb5fa4f3b61de
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="object-map-macros"></a>Macros de mapa de objeto
Estas macros definen entradas y asignaciones de objeto.  
  
|||  
|-|-|  
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Permite especificar la descripción de texto del objeto de clase, que se escribirá en el mapa de objetos.|  
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Escribe un objeto ATL en el mapa de objetos, actualiza el registro y crea una instancia del objeto.|  
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Le permite especificar que el objeto debe estar registrado e inicializado, pero no se debe poder crear externamente que se pueden crear con `CoCreateInstance`.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
   
##  <a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION  
 Permite especificar una descripción de texto para el objeto class.  
  
```
DECLARE_OBJECT_DESCRIPTION( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] Descripción del objeto de clase.  
  
### <a name="remarks"></a>Comentarios  
 ATL entra esta descripción en el mapa de objetos a través de la [objeto OBJECT_ENTRY](http://msdn.microsoft.com/en-us/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd) macro.  
  
 `DECLARE_OBJECT_DESCRIPTION`implementa un `GetObjectDescription` función, que puede usar para invalidar la [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription) método.  

  
 El `GetObjectDescription` función es invocada por **IComponentRegistrar::GetComponents**. **IComponentRegistrar** es una interfaz de automatización que le permite registrar y anular el registro de componentes individuales en un archivo DLL. Cuando se crea un objeto de registro del componente con el Asistente para proyectos ATL, el Asistente implementará automáticamente el **IComponentRegistrar** interfaz. **IComponentRegistrar** se utiliza normalmente con Microsoft Transaction Server.  
  
 Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#123;](../../atl/codesnippet/cpp/object-map-macros_1.h)]  
  
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
  
 `OBJECT_ENTRY_AUTO`Introduce los punteros de función de la clase de creador y la clase de generador de clases creador `CreateInstance` las funciones de este objeto en el mapa de objetos ATL generado automáticamente. Cuando [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) es llama, actualiza el registro del sistema para cada objeto del mapa de objetos.  

  
 La siguiente tabla describe cómo se obtiene la información que se agrega al mapa de objetos de la clase que se proporcionó como el segundo parámetro para esta macro.  
  
|Información de|Obtenido de|  
|---------------------|-------------------|  
|Registro COM|[Macros de registro](../../atl/reference/registry-macros.md)|  
|Creación del generador de clases|[Macros de clase de fábrica](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Creación de instancias|[Macros de agregación](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Registro de la categoría de componentes|[Macros de categoría](../../atl/reference/category-macros.md)|  
|Inicialización de nivel de clase y limpieza|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

  
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
  
 `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO`permite especificar que un objeto debe ser registrado e inicializado (consulte [OBJECT_ENTRY_AUTO](#object_entry_auto) para obtener más información), pero no deben crear a través de `CoCreateInstance`.  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)

