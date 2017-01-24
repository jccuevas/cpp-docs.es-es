---
title: "IRowsetUpdateImpl::m_mapCachedData | Microsoft Docs"
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
  - "IRowsetUpdateImpl.m_mapCachedData"
  - "IRowsetUpdateImpl::m_mapCachedData"
  - "m_mapCachedData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_mapCachedData"
ms.assetid: 65131743-8580-48c8-bb22-68f17c9dfa13
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::m_mapCachedData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un mapa que contiene los datos originales para la operación diferida.  
  
## Sintaxis  
  
```  
  
      CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### Parámetros  
 `hRow`  
 Identificador a las filas de los datos.  
  
 `pData`  
 Un puntero a los datos que se va a almacenar en memoria caché.  Los datos se *de almacenamiento* tipo \(la clase de registro de usuario\).  Vea el argumento de plantilla *de almacenamiento* en [Clase IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md).  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetUpdateImpl \(Clase\)](../../data/oledb/irowsetupdateimpl-class.md)