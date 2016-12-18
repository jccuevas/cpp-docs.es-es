---
title: "CDataSource::GetInitializationString | Microsoft Docs"
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
  - "ATL::CDataSource::GetInitializationString"
  - "CDataSource.GetInitializationString"
  - "GetInitializationString"
  - "CDataSource::GetInitializationString"
  - "ATL.CDataSource.GetInitializationString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInitializationString (método)"
ms.assetid: 97134723-6e99-4004-a56d-ec57543dbf3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataSource::GetInitializationString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera la cadena de inicialización de un origen de datos que está actualmente abierto.  
  
## Sintaxis  
  
```  
  
      HRESULT GetInitializationString(   
   BSTR* pInitializationString,   
   bool bIncludePassword = false    
) throw( );  
```  
  
#### Parámetros  
 *el pInitializationString*  
 \[out\] Un puntero a la cadena de inicialización.  
  
 *bIncludePassword*  
 \[in\] **true** si la cadena incluye una contraseña; si no **false**.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 La cadena de inicialización resultante se puede usar para volver a abrir posteriormente esta conexión a un origen de datos.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataSource \(Clase\)](../../data/oledb/cdatasource-class.md)