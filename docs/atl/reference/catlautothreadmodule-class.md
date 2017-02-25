---
title: "CAtlAutoThreadModule Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlAutoThreadModule"
  - "CAtlAutoThreadModule"
  - "ATL::CAtlAutoThreadModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlAutoThreadModule class"
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CAtlAutoThreadModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa subproceso\-haber agrupado, servidor COM de apartamento\-modelo.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      class CAtlAutoThreadModule :  
public CAtlAutoThreadModuleT< CAtlAutoThreadModule >  
```  
  
## Comentarios  
 `CAtlAutoThreadModule` deriva de [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) e implementa subproceso\- haber agrupado, servidor COM de apartamento\- modelo.  `CAtlAutoThreadModule` utiliza [CComApartment](../../atl/reference/ccomapartment-class.md) para administrar un apartamento para cada subproceso del módulo.  
  
 Debe utilizar la macro de [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) en la definición de clase del objeto para especificar [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de la clase.  Debe agregar una instancia única de una clase derivada de `CAtlAutoThreadModuleT` como `CAtlAutoThreadModule`.  Por ejemplo:  
  
 `CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`  
  
> [!NOTE]
>  Esta clase reemplaza la clase obsoletos de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) .  
  
## Jerarquía de herencia  
 `IAtlAutoThreadModule`  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 `CAtlAutoThreadModule`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [CAtlAutoThreadModuleT Class](../../atl/reference/catlautothreadmodulet-class.md)   
 [IAtlAutoThreadModule Class](../../atl/reference/iatlautothreadmodule-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)