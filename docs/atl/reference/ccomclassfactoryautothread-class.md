---
title: "CComClassFactoryAutoThread Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComClassFactoryAutoThread"
  - "ATL.CComClassFactoryAutoThread"
  - "CComClassFactoryAutoThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactoryAutoThread class"
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComClassFactoryAutoThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa la interfaz de [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) , y permite que los objetos se crean en apartamentos múltiples.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      class CComClassFactoryAutoThread : public IClassFactory,   
public CComObjectRootEx< CComGlobalsThreadModel >  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComClassFactoryAutoThread::CreateInstance](../Topic/CComClassFactoryAutoThread::CreateInstance.md)|crea un objeto de CLSID especificado.|  
|[CComClassFactoryAutoThread::LockServer](../Topic/CComClassFactoryAutoThread::LockServer.md)|Bloquea la generador de clases en memoria.|  
  
## Comentarios  
 `CComClassFactoryAutoThread` es similar a [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), pero permite que los objetos se crean en apartamentos múltiples.  Para aprovecharse de esta compatibilidad, derive el módulo EXE de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Objetos ATL adquieren normalmente un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md).  Esta clase incluye [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)macros, que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) mientras el generador predeterminada de la clase.  Para utilizar `CComClassFactoryAutoThread`, especifique la macro de [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) en la definición de clase del objeto.  Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/CPP/ccomclassfactoryautothread-class_1.h)]  
  
## Jerarquía de herencia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 `CComClassFactoryAutoThread`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 Class](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactorySingleton Class](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)