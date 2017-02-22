---
title: "CManualAccessor::AddBindEntry | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CManualAccessor::AddBindEntry"
  - "ATL.CManualAccessor.AddBindEntry"
  - "CManualAccessor::AddBindEntry"
  - "AddBindEntry"
  - "CManualAccessor.AddBindEntry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddBindEntry (método)"
ms.assetid: 8556dda9-dda1-4f67-96bc-6031e6c6a271
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CManualAccessor::AddBindEntry
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Agrega una entrada de enlace a las columnas de salida.  
  
## Sintaxis  
  
```  
  
      void AddBindEntry(  
   DBORDINAL nOrdinal,  
   DBTYPE wType,  
   DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL   
) throw ( );  
```  
  
#### Parámetros  
 Vea [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) en *la referencia del*programador.  
  
 `nOrdinal`  
 \[in\] Número de columnas.  
  
 `wType`  
 \[in\] Tipo de datos.  
  
 `nColumnSize`  
 \[in\] Tamaño de la columna en bytes.  
  
 `pData`  
 \[in\] Un puntero a los datos de columna almacenados en el búfer.  
  
 `pLength`  
 \[in\] Un puntero a la longitud de campo, si es necesario.  
  
 `pStatus`  
 \[in\] Un puntero a la variable que se enlazará el estado de la columna, si es necesario.  
  
## Comentarios  
 Para utilizar esta función, debe llamar primero a [CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md).  No puede agregar varias entradas que el número de columnas especificadas en `CreateAccessor`.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CManualAccessor \(Clase\)](../../data/oledb/cmanualaccessor-class.md)   
 [Ejemplo de DBViewer](../../top/visual-cpp-samples.md)