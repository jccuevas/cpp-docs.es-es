---
title: "CComDynamicUnkArray Class | Microsoft Docs"
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
  - "ATL.CComDynamicUnkArray"
  - "CComDynamicUnkArray"
  - "ATL::CComDynamicUnkArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComDynamicUnkArray class"
  - "puntos de conexión [C++], administrar"
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComDynamicUnkArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase almacena una matriz de punteros de **IUnknown** .  
  
## Sintaxis  
  
```  
class CComDynamicUnkArray  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComDynamicUnkArray::CComDynamicUnkArray](../Topic/CComDynamicUnkArray::CComDynamicUnkArray.md)|Constructor.  Inicializa los valores de la colección a **NULL** y el tamaño de la colección en cero.|  
|[CComDynamicUnkArray::~CComDynamicUnkArray](../Topic/CComDynamicUnkArray::~CComDynamicUnkArray.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComDynamicUnkArray::Add](../Topic/CComDynamicUnkArray::Add.md)|Llame a este método para agregar un puntero de `IUnknown` a la matriz.|  
|[CComDynamicUnkArray::begin](../Topic/CComDynamicUnkArray::begin.md)|Devuelve un puntero al primer puntero de `IUnknown` en la colección.|  
|[CComDynamicUnkArray::clear](../Topic/CComDynamicUnkArray::clear.md)|Vacía la matriz.|  
|[CComDynamicUnkArray::end](../Topic/CComDynamicUnkArray::end.md)|Devuelve un puntero a uno más allá del puntero último de **IUnknown** en la colección.|  
|[CComDynamicUnkArray::GetAt](../Topic/CComDynamicUnkArray::GetAt.md)|Recupera el elemento en el índice especificado.|  
|[CComDynamicUnkArray::GetCookie](../Topic/CComDynamicUnkArray::GetCookie.md)|Llame a este método para obtener la cookie asociada a un puntero determinado de **IUnknown** .|  
|[CComDynamicUnkArray::GetSize](../Topic/CComDynamicUnkArray::GetSize.md)|Devuelve la longitud de una matriz.|  
|[CComDynamicUnkArray::GetUnknown](../Topic/CComDynamicUnkArray::GetUnknown.md)|Llame a este método para obtener el puntero de **IUnknown** asociado a una cookie especificada.|  
|[CComDynamicUnkArray::Remove](../Topic/CComDynamicUnkArray::Remove.md)|Llame a este método para quitar un puntero de **IUnknown** de la matriz.|  
  
## Comentarios  
 **CComDynamicUnkArray** contiene una matriz dinámicamente asignado de punteros de **IUnknown** , cada una interfaz en un punto de conexión.  **CComDynamicUnkArray** se puede utilizar como un parámetro a la clase de plantilla de [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .  
  
 Los métodos [inicio](../Topic/CComDynamicUnkArray::begin.md) y [final](../Topic/CComDynamicUnkArray::end.md) de **CComDynamicUnkArray** se pueden utilizar para recorrer en iteración todos los puntos de conexión \(por ejemplo, cuando se desencadena un evento\).  
  
 Vea [Adding Connection Points to an Object](../../atl/adding-connection-points-to-an-object.md) para obtener detalles sobre la automatización de creación de proxies de punto de conexión.  
  
> [!NOTE]
>  La clase **CComDynamicUnkArray** de**Note** Z es utilizada por el asistente de **Agregar clase** al crear un control que tiene puntos de Conexión.  Si desea especificar el número de puntos de Conexión manualmente, cambie la referencia de **CComDynamicUnkArray***a n* `>`de `CComUnkArray<`, donde *n* es el número de puntos de conexión necesarios.  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComUnkArray Class](../../atl/reference/ccomunkarray-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)