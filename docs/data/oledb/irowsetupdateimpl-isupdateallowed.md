---
title: "IRowsetUpdateImpl::IsUpdateAllowed | Microsoft Docs"
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
  - "IRowsetUpdateImpl::IsUpdateAllowed"
  - "IRowsetUpdateImpl.IsUpdateAllowed"
  - "IsUpdateAllowed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsUpdateAllowed (método)"
ms.assetid: d6daf3b3-a8e0-4275-a67d-897dea01e297
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::IsUpdateAllowed
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Invalide este método para comprobar la seguridad, integridad, etc. antes de actualizaciones.  
  
## Sintaxis  
  
```  
  
      HRESULT IsUpdateAllowed(  
   DBPENDINGSTATUS /* [in] *//* status */,  
   HROW /* [in] *//* hRowUpdate */,  
   DBROWSTATUS* /* [out] *//* pRowStatus */  
);  
```  
  
#### Parámetros  
 *status*  
 \[in\] El estado de operaciones pendientes en las filas.  
  
 *hRowUpdate*  
 \[in\] Administrar para las filas que desea actualizar.  
  
 *pRowStatus*  
 \[out\] El estado devuelto al usuario.  
  
## Comentarios  
 Si determina que una actualización debe ser permitida, devuelve `S_OK`; si no devuelve **E\_FAIL**.  Si permite una actualización, también debe establecer **DBROWSTATUS** en [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) a [estado de fila](https://msdn.microsoft.com/en-us/library/ms722752.aspx)adecuado.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetUpdateImpl \(Clase\)](../../data/oledb/irowsetupdateimpl-class.md)