---
title: "CDataSource::GetProperty | Microsoft Docs"
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
  - "ATL::CDataSource::GetProperty"
  - "ATL.CDataSource.GetProperty"
  - "CDataSource.GetProperty"
  - "CDataSource::GetProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProperty (método)"
ms.assetid: 6531147c-b164-4ab5-a4a7-509634b85b4d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataSource::GetProperty
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el valor de una propiedad especificada para el objeto de origen de datos conectado.  
  
## Sintaxis  
  
```  
  
      HRESULT GetProperty(   
   const GUID& guid,   
   DBPROPID propid,   
   VARIANT* pVariant    
) const throw( );  
```  
  
#### Parámetros  
 `guid`  
 \[in\] GUID que identifica la propiedad establecida en qué devuelve la propiedad.  
  
 `propid`  
 \[in\] Identificador de propiedad para la propiedad vuelva.  
  
 *pVariant*  
 \[out\] Un puntero a la variante donde **GetProperty** devuelve el valor de la propiedad.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Para obtener varias propiedades, utilice [GetProperties](../../data/oledb/cdatasource-getproperties.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataSource \(Clase\)](../../data/oledb/cdatasource-class.md)