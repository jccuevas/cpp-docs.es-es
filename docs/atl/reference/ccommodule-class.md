---
title: "CComModule Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComModule class"
  - "DLL modules [C++], ATL"
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CComModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

A partir de ATL 7,0, está desusada `CComModule` : vea [Clases de módulo ATL](../../atl/atl-module-classes.md) para más detalles.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
class CComModule : public _ATL_MODULE  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComModule::GetClassObject](../Topic/CComModule::GetClassObject.md)|crea un objeto de CLSID especificado.  Sólo para DLLs.|  
|[CComModule::GetModuleInstance](../Topic/CComModule::GetModuleInstance.md)|Devuelva `m_hInst`.|  
|[CComModule::GetResourceInstance](../Topic/CComModule::GetResourceInstance.md)|Devuelva `m_hInstResource`.|  
|[CComModule::GetTypeLibInstance](../Topic/CComModule::GetTypeLibInstance.md)|Devuelva `m_hInstTypeLib`.|  
|[CComModule::Init](../Topic/CComModule::Init.md)|se inicializan los miembros de datos.|  
|[CComModule::RegisterClassHelper](../Topic/CComModule::RegisterClassHelper.md)|Escribe el registro estándar de la clase de un objeto del sistema.|  
|[CComModule::RegisterClassObjects](../Topic/CComModule::RegisterClassObjects.md)|Registra el objeto de clase.  Para los ensamblados EXE únicamente.|  
|[CComModule::RegisterServer](../Topic/CComModule::RegisterServer.md)|Actualiza el sistema para cada objeto del mapa del objeto.|  
|[CComModule::RegisterTypeLib](../Topic/CComModule::RegisterTypeLib.md)|registra una biblioteca de tipos.|  
|[CComModule::RevokeClassObjects](../Topic/CComModule::RevokeClassObjects.md)|Revoca el objeto de clase.  Para los ensamblados EXE únicamente.|  
|[CComModule::Term](../Topic/CComModule::Term.md)|Miembros de datos de versiones.|  
|[CComModule::UnregisterClassHelper](../Topic/CComModule::UnregisterClassHelper.md)|Quita el registro estándar de la clase de un objeto de registro del sistema.|  
|[CComModule::UnregisterServer](../Topic/CComModule::UnregisterServer.md)|Anula cada objeto del mapa del objeto.|  
|[CComModule::UpdateRegistryClass](../Topic/CComModule::UpdateRegistryClass.md)|Registros o anula el registro estándar de la clase de un objeto.|  
|[CComModule::UpdateRegistryFromResourceD](../Topic/CComModule::UpdateRegistryFromResourceD.md)|Ejecute el script contenido en el recurso especificado al que se utiliza con un objeto.|  
|[CComModule::UpdateRegistryFromResourceS](../Topic/CComModule::UpdateRegistryFromResourceS.md)|Estáticamente vínculos al componente de registro ATL.  Ejecute el script contenido en el recurso especificado al que se utiliza con un objeto.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComModule::m\_csObjMap](../Topic/CComModule::m_csObjMap.md)|Ensures sincronizó el acceso a la información del mapa del objeto.|  
|[CComModule::m\_csTypeInfoHolder](../Topic/CComModule::m_csTypeInfoHolder.md)|Ensures sincronizó el acceso a la información de la biblioteca de tipos.|  
|[CComModule::m\_csWindowCreate](../Topic/CComModule::m_csWindowCreate.md)|Ensures sincronizó el acceso a la información de la clase de ventana y datos estáticos utilizados durante la creación de la ventana.|  
|[CComModule::m\_hInst](../Topic/CComModule::m_hInst.md)|Contiene el identificador de la instancia del módulo.|  
|[CComModule::m\_hInstResource](../Topic/CComModule::m_hInstResource.md)|De forma predeterminada, contiene el identificador de la instancia del módulo.|  
|[CComModule::m\_hInstTypeLib](../Topic/CComModule::m_hInstTypeLib.md)|De forma predeterminada, contiene el identificador de la instancia del módulo.|  
|[CComModule::m\_pObjMap](../Topic/CComModule::m_pObjMap.md)|Señala al mapa de objetos mantenido por la instancia del módulo.|  
  
## Comentarios  
  
> [!NOTE]
>  Se deja de utilizar esta clase, y los asistentes de generación de código ATL ahora utilizan las clases derivadas de [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) y de [CAtlModule](../../atl/reference/catlmodule-class.md) .  Vea [Clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más información.  La información que sigue es para el uso con aplicaciones creadas con anteriores versiones ATL.  `CComModule` sigue siendo parte de ATL por hacia atrás capacidad.  
  
 `CComModule` implementa un módulo de servidor COM, lo que un cliente tiene acceso a los componentes de módulo.  `CComModule` admite módulos de DLL \(en proceso\) y EXE \(local\).  
  
 Una instancia de `CComModule` utiliza un mapa del objeto para mantener un conjunto de definiciones de objeto de la clase.  Este mapa de objetos se implementa como una matriz de estructuras de `_ATL_OBJMAP_ENTRY` , y contiene información para:  
  
-   Escribir y quitando descripciones de objeto del sistema.  
  
-   Crear instancias de objetos a través de un generador de clases.  
  
-   Establecimiento de la comunicación entre un cliente y el objeto del componente.  
  
-   Realizar la administración de la duración de los objetos de la clase.  
  
 Cuando se ejecuta el ATL AppWizard COM, el asistente genera automáticamente `_Module`, una instancia global de `CComModule` o una clase derivada de ella.  Para obtener más información sobre el asistente para proyectos ATL, vea el artículo [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).  
  
 Además de `CComModule`, ATL proporciona [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), que implementa un módulo de apartamento\-modelo para EXE y servicios de Windows.  Derive el módulo de `CComAutoThreadModule` cuando desee crear objetos en apartamentos múltiples.  
  
## Jerarquía de herencia  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CComModule`  
  
## Requisitos  
 `Header:` atlbase.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)