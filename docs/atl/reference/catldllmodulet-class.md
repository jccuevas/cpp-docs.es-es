---
title: "CAtlDllModuleT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlDllModuleT"
  - "ATL::CAtlDllModuleT<T>"
  - "ATL::CAtlDllModuleT"
  - "ATL.CAtlDllModuleT<T>"
  - "CAtlDllModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlDllModuleT class"
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CAtlDllModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa el módulo del archivo DLL.  
  
## Sintaxis  
  
```  
  
      template <  
   class T   
>  
class ATL_NO_VTABLE CAtlDllModuleT :  
   public CAtlModuleT< T >  
```  
  
#### Parámetros  
 `T`  
 la clase derivada de `CAtlDllModuleT`.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlDllModuleT::CAtlDllModuleT](../Topic/CAtlDllModuleT::CAtlDllModuleT.md)|el constructor.|  
|[CAtlDllModuleT::~CAtlDllModuleT](../Topic/CAtlDllModuleT::~CAtlDllModuleT.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlDllModuleT::DllCanUnloadNow](../Topic/CAtlDllModuleT::DllCanUnloadNow.md)|Comprueba si el archivo DLL puede descargar.|  
|[CAtlDllModuleT::DllGetClassObject](../Topic/CAtlDllModuleT::DllGetClassObject.md)|Devuelve un generador de clases.|  
|[CAtlDllModuleT::DllMain](../Topic/CAtlDllModuleT::DllMain.md)|El punto de entrada opcional en una biblioteca de vínculos dinámicos \(DLL\).|  
|[CAtlDllModuleT::DllRegisterServer](../Topic/CAtlDllModuleT::DllRegisterServer.md)|Agrega entradas en el registro del sistema para los objetos de DLL.|  
|[CAtlDllModuleT::DllUnregisterServer](../Topic/CAtlDllModuleT::DllUnregisterServer.md)|Quita entradas en el registro del sistema para los objetos de DLL.|  
|[CAtlDllModuleT::GetClassObject](../Topic/CAtlDllModuleT::GetClassObject.md)|Devuelve un generador de clases.  Invocado por [DllGetClassObject](../Topic/CAtlDllModuleT::DllGetClassObject.md).|  
  
## Comentarios  
 `CAtlDllModuleT` representa el módulo para una biblioteca de vínculos dinámicos \(DLL\) y proporciona funciones utilizadas por todos los proyectos de DLL.  Esta forma de la clase de [CAtlModuleT](../../atl/reference/catlmodulet-class.md) incluye compatibilidad para el registro.  
  
 Para obtener más información sobre los módulos de ATL, vea [Clases de módulo ATL](../../atl/atl-module-classes.md).  
  
## Jerarquía de herencia  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlDllModuleT`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [CAtlModuleT Class](../../atl/reference/catlmodulet-class.md)   
 [CAtlExeModuleT Class](../../atl/reference/catlexemodulet-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)