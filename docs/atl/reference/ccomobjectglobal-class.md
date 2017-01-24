---
title: "CComObjectGlobal Class | Microsoft Docs"
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
  - "CComObjectGlobal"
  - "ATL::CComObjectGlobal<Base>"
  - "ATL::CComObjectGlobal"
  - "ATL.CComObjectGlobal"
  - "ATL.CComObjectGlobal<Base>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectGlobal class"
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObjectGlobal Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase administra un recuento de referencias en el módulo que contiene el objeto de `Base` .  
  
## Sintaxis  
  
```  
  
      template<  
   class Base   
>  
class CComObjectGlobal :  
   public Base  
```  
  
#### Parámetros  
 `Base`  
 La clase, derivadas de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), además de cualquier otra interfaz desea admitir en el objeto.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectGlobal::CComObjectGlobal](../Topic/CComObjectGlobal::CComObjectGlobal.md)|el constructor.|  
|[CComObjectGlobal::~CComObjectGlobal](../Topic/CComObjectGlobal::~CComObjectGlobal.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectGlobal::AddRef](../Topic/CComObjectGlobal::AddRef.md)|implementa `AddRef`global.|  
|[CComObjectGlobal::QueryInterface](../Topic/CComObjectGlobal::QueryInterface.md)|implementa `QueryInterface`global.|  
|[CComObjectGlobal::Release](../Topic/CComObjectGlobal::Release.md)|implementa **Liberar**global.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectGlobal::m\_hResFinalConstruct](../Topic/CComObjectGlobal::m_hResFinalConstruct.md)|Contiene **HRESULT** devuelto durante la construcción del objeto de `CComObjectGlobal` .|  
  
## Comentarios  
 `CComObjectGlobal` administra un recuento de referencias en el módulo que contiene el objeto de `Base` .  `CComObjectGlobal` garantiza el objeto no se eliminará mientras el módulo no se libere.  El objeto se quitará sólo cuando el recuento de referencias en el módulo completo va a cero.  
  
 Por ejemplo, mediante `CComObjectGlobal`, un generador de clases puede contener un objeto global común compartido por todos los clientes.  
  
## Jerarquía de herencia  
 `Base`  
  
 `CComObjectGlobal`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComObjectStack Class](../../atl/reference/ccomobjectstack-class.md)   
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)