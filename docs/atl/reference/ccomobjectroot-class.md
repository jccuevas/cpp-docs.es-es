---
title: "CComObjectRoot Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComObjectRoot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectRoot class"
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CComObjectRoot Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este typedef de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) templatized en el modelo de subprocesos predeterminado del servidor.  
  
## Sintaxis  
  
```  
  
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;  
  
```  
  
## Comentarios  
 `CComObjectRoot` es `typedef` de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) templatized en el modelo de subprocesos predeterminado del servidor.  así [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) hará referencia [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md).  
  
 administración del recuento de referencias de objeto de los identificadores de`CComObjectRootEx` para los objetos nonaggregated y agregados.  Contiene el recuento de referencias de objeto si el objeto no se suma, y mantiene el puntero a desconocido externo si se está agregando el objeto.  Para los objetos agregados, los métodos de `CComObjectRootEx` se pueden utilizar para controlar el error del objeto interno a la construcción, y proteger el objeto externo de eliminación cuando se publican interfaces internas o el objeto interno se elimina.  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComObjectRootEx Class Members](http://msdn.microsoft.com/es-es/e3ce9c3d-9c8e-4fe5-b682-8e56740a0164)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)