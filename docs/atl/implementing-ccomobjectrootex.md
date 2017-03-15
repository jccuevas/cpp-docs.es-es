---
title: "Implementing CComObjectRootEx | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CComObjectRootEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectRoot class, implementar"
  - "CComObjectRootEx class"
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Implementing CComObjectRootEx
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) es fundamental. Todos los objetos ATL deben tener una instancia de `CComObjectRootEx` o [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) en su herencia.  `CComObjectRootEx` ofrece el mecanismo de `QueryInterface` predeterminado basado en entradas de asignación COM.  
  
 A través de esta asignación COM, las interfaces de un objeto se exponen a un cliente cuando este realiza una consulta sobre una interfaz.  La consulta se tramita a través de `CComObjectRootEx::InternalQueryInterface`.  `InternalQueryInterface` solo administra interfaces de la tabla de asignación COM.  
  
 Para especificar interfaces en la tabla de asignación COM, puede usar la macro [COM\_INTERFACE\_ENTRY](../Topic/COM_INTERFACE_ENTRY%20\(ATL\).md) o cualquiera de sus variantes.  Por ejemplo, en el siguiente código se especifican las interfaces `IDispatch`, `IBeeper` y `ISupportErrorInfo` en la tabla de asignación COM:  
  
 [!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/CPP/implementing-ccomobjectrootex_1.h)]  
  
## Vea también  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)   
 [COM Map Macros](../atl/reference/com-map-macros.md)