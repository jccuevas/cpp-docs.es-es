---
title: "CDynamicAccessor::SetBlobHandling | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicAccessor::SetBlobHandling"
  - "CDynamicAccessor.SetBlobHandling"
  - "ATL::CDynamicAccessor::SetBlobHandling"
  - "SetBlobHandling"
  - "ATL.CDynamicAccessor.SetBlobHandling"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetBlobHandling (método)"
ms.assetid: fa8b0bb3-a21b-4d64-aeef-e79bf61d079c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::SetBlobHandling
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece BLOB que administra el valor de la fila actual.  
  
## Sintaxis  
  
```  
  
      bool SetBlobHandling(  
   DBBLOBHANDLINGENUM eBlobHandling   
);  
```  
  
#### Parámetros  
 `eBlobHandling`  
 Especifica cómo los datos de BLOB debe ser administrado.  Puede tomar los valores siguientes:  
  
-   **DBBLOBHANDLING\_DEFAULT**: Controlar los datos de columna más largos que `nBlobSize` \(como lo establece `SetBlobSizeLimit`\) como datos de BLOB y recuperelos a través de un objeto de `ISequentialStream` o de `IStream` .  Esta opción intentará enlazar cada columna que contiene los datos mayores que `nBlobSize` o enumerados como **DBTYPE\_IUNKNOWN** como datos de BLOB.  
  
-   **DBBLOBHANDLING\_NOSTREAMS**: Controlar los datos de columna más largos que `nBlobSize` \(como lo establece `SetBlobSizeLimit`\) como datos de BLOB y recuperelos con referencia en memoria proveedor\- asignada, consumidor\- poseída.  Esta opción es útil para las tablas que tienen más de una columna de BLOB, y el proveedor sólo admite un objeto de `ISequentialStream` por descriptor.  
  
-   **DBBLOBHANDLING\_SKIP**: Omitir \(no haga enlace\) columnas que calificaban que contienen objetos binarios \(el descriptor de acceso no enlazará ni recuperará el valor de la columna pero todavía se recuperará el estado y la longitud de la columna\).  
  
## Comentarios  
 Debe llamar a `SetBlobHandling` antes de llamar a **Abierta**.  
  
 El método [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) de constructor establece BLOB que administra valor a **DBBLOBHANDLING\_DEFAULT**.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)