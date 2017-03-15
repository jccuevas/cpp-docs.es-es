---
title: "CCommand::GetNextResult | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CCommand::GetNextResult"
  - "CCommand::GetNextResult"
  - "GetNextResult"
  - "CCommand.GetNextResult"
  - "ATL.CCommand.GetNextResult"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetNextResult (método)"
ms.assetid: 63df9b55-9490-45c4-934a-879c5c2725d8
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CCommand::GetNextResult
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene el conjunto de resultados siguiente si uno disponible.  
  
## Sintaxis  
  
```  
  
      HRESULT GetNextResult(  
   DBROWCOUNT* pulRowsAffected,  
   bool bBind = true   
) throw( );  
```  
  
#### Parámetros  
 *pulRowsAffected*  
 \[in\/out\] Un puntero a la memoria donde el recuento de filas afectadas por un comando se devuelve.  
  
 `bBind`  
 \[in\] Especifica si enlazar el comando automáticamente después de ejecutarse.  El valor predeterminado es **true**, que hace que el comando de enlazarse automáticamente.  El valor `bBind` a **false** evita el enlace automático del comando para que pueda enlazar manualmente. \(El enlace manual resulta especialmente interesante para los usuarios de OLAP\).  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Si se ha capturado un conjunto de resultados previamente, libera de esta función el conjunto de resultados anterior y desatan las columnas.  Si `bBind` es **true**, enlaza las nuevas columnas.  
  
 Debe llamar a esta función sólo si ha especificado varios resultados estableciendo el parámetro *TMultiple\=*`CMultipleResults`de la plantilla de `CCommand` .  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CCommand \(Clase\)](../../data/oledb/ccommand-class.md)