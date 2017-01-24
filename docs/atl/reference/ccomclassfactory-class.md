---
title: "CComClassFactory Class | Microsoft Docs"
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
  - "ATL.CComClassFactory"
  - "CComClassFactory"
  - "ATL::CComClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactory class"
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComClassFactory Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa la interfaz de [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) .  
  
## Sintaxis  
  
```  
  
   class CComClassFactory : public IClassFactory,   
public CComObjectRootEx< CComGlobalsThreadModel >  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComClassFactory::CreateInstance](../Topic/CComClassFactory::CreateInstance.md)|crea un objeto de CLSID especificado.|  
|[CComClassFactory::LockServer](../Topic/CComClassFactory::LockServer.md)|Bloquea la generador de clases en memoria.|  
  
## Comentarios  
 `CComClassFactory` implementa la interfaz de [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) , que contiene los métodos para crear un objeto de CLSID determinado, así como bloquea la generador de clases en memoria para permitir que los nuevos objetos se crean más rápidamente.  **IClassFactory** se debe implementar para cada clase que se registre en el sistema y a la que asigna el CLSID.  
  
 Objetos ATL adquieren normalmente un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md).  Esta clase incluye [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)macros, que declara `CComClassFactory` mientras el generador predeterminada de la clase.  Para invalidar este valor predeterminado, especifique una de las macros de `DECLARE_CLASSFACTORY`*XXX* en la definición de clase.  Por ejemplo, la macro de [DECLARE\_CLASSFACTORY\_EX](../Topic/DECLARE_CLASSFACTORY_EX.md) utiliza la clase especificada para el generador de clases:  
  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/CPP/ccomclassfactory-class_1.h)]  
  
 La definición de clase anterior especifica que **CMyClassFactory** se utilizará como generador predeterminada de la clase del objeto.  **CMyClassFactory** debe derivar de `CComClassFactory` y reemplazar `CreateInstance`.  
  
 ATL proporciona otras tres macros que declare un generador de clases:  
  
-   [DECLARE\_CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) utiliza [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), que controla la creación a través de una licencia.  
  
-   [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) utiliza [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), que crea objetos en apartamentos múltiples.  
  
-   [DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md) utiliza [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), que crea un único objeto de [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) .  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)