---
title: "CComClassFactorySingleton Class | Microsoft Docs"
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
  - "ATL.CComClassFactorySingleton"
  - "ATL.CComClassFactorySingleton<T>"
  - "ATL::CComClassFactorySingleton"
  - "ATL::CComClassFactorySingleton<T>"
  - "CComClassFactorySingleton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactorySingleton class"
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComClassFactorySingleton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un único objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
class T  
>  
class CComClassFactorySingleton :  
public CComClassFactory  
```  
  
#### Parámetros  
 `T`  
 la clase.  
  
 `CComClassFactorySingleton` deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un único objeto.  Cada llamada de `CreateInstance` de método a las consultas simplemente este objeto para un puntero de interfaz.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComClassFactorySingleton::CreateInstance](../Topic/CComClassFactorySingleton::CreateInstance.md)|Consultas `m_spObj` para un puntero de interfaz.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComClassFactorySingleton::m\_spObj](../Topic/CComClassFactorySingleton::m_spObj.md)|el objeto de [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) construido por `CComClassFactorySingleton`.|  
  
## Comentarios  
 Objetos ATL adquieren normalmente un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md).  Esta clase incluye [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)macros, que declara `CComClassFactory` mientras el generador predeterminada de la clase.  Para utilizar `CComClassFactorySingleton`, especifique la macro de [DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md) en la definición de clase del objeto.  Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/CPP/ccomclassfactorysingleton-class_1.h)]  
  
## Jerarquía de herencia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)  
  
 `CComClassFactorySingleton`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 Class](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactoryAutoThread Class](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)