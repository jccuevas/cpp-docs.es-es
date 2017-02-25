---
title: "CComUnkArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComUnkArray"
  - "ATL.CComUnkArray<nMaxSize>"
  - "ATL::CComUnkArray<nMaxSize>"
  - "ATL::CComUnkArray"
  - "CComUnkArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComUnkArray class"
  - "puntos de conexión [C++], administrar"
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CComUnkArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase almacena los punteros de **IUnknown** , y es utilizada como parámetro a la clase de plantilla de [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .  
  
## Sintaxis  
  
```  
template<  
   unsigned int nMaxSize  
>  
class CComUnkArray  
```  
  
#### Parámetros  
 *nMaxSize*  
 El número máximo de punteros de **IUnknown** que se pueden almacenar en la matriz estático.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComUnkArray::CComUnkArray](../Topic/CComUnkArray::CComUnkArray.md)|Constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComUnkArray::Add](../Topic/CComUnkArray::Add.md)|Llame a este método para agregar un puntero de **IUnknown** a la matriz.|  
|[CComUnkArray::begin](../Topic/CComUnkArray::begin.md)|Devuelve un puntero al primer puntero de **IUnknown** en la colección.|  
|[CComUnkArray::end](../Topic/CComUnkArray::end.md)|Devuelve un puntero a uno más allá del puntero último de **IUnknown** en la colección.|  
|[CComUnkArray::GetCookie](../Topic/CComUnkArray::GetCookie.md)|Llame a este método para obtener la cookie asociada a un puntero determinado de **IUnknown** .|  
|[CComUnkArray::GetUnknown](../Topic/CComUnkArray::GetUnknown.md)|Llame a este método para obtener el puntero de **IUnknown** asociado a una cookie especificada.|  
|[CComUnkArray::Remove](../Topic/CComUnkArray::Remove.md)|Llame a este método para quitar un puntero de **IUnknown** de la matriz.|  
  
## Comentarios  
 **CComUnkArray** mantiene un número fijo de punteros de **IUnknown** , cada una interfaz en un punto de conexión.  **CComUnkArray** se puede utilizar como un parámetro a la clase de plantilla de [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .  **CComUnkArray\<1\>** es una especialización de plantilla de **CComUnkArray** que se ha optimizado para un punto de conexión.  
  
 Los métodos [inicio](../Topic/CComUnkArray::begin.md) y [final](../Topic/CComUnkArray::end.md) de **CComUnkArray** se pueden utilizar para recorrer en iteración todos los puntos de conexión \(por ejemplo, cuando se desencadena un evento\).  
  
 Vea [Adding Connection Points to an Object](../../atl/adding-connection-points-to-an-object.md) para obtener detalles sobre la automatización de creación de proxies de punto de conexión.  
  
> [!NOTE]
>  La clase [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) de**Note** Z es utilizada por el asistente de **Agregar clase** al crear un control que tiene puntos de Conexión.  Si desea especificar el número de puntos de Conexión manualmente, cambie la referencia de **CComDynamicUnkArray***a n* `>`de `CComUnkArray<`, donde *n* es el número de puntos de conexión necesarios.  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComDynamicUnkArray Class](../../atl/reference/ccomdynamicunkarray-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)