---
title: "CDynamicAccessor::GetColumnInfo | Microsoft Docs"
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
  - "GetColumnInfo"
  - "ATL.CDynamicAccessor.GetColumnInfo"
  - "ATL::CDynamicAccessor::GetColumnInfo"
  - "CDynamicAccessor.GetColumnInfo"
  - "CDynamicAccessor::GetColumnInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnInfo (método)"
ms.assetid: 7f2102ea-b7cc-4714-812f-3ca2857f4b9a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::GetColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve los metadatos de columna que necesitan la mayoría de los consumidores.  
  
## Sintaxis  
  
```  
  
      HRESULT GetColumnInfo(   
   IRowset* pRowset,   
   DBORDINAL* pColumns,   
   DBCOLUMNINFO** ppColumnInfo,   
   OLECHAR** ppStringsBuffer    
) throw( );  
```  
  
#### Parámetros  
 `pRowset`  
 \[in\] Un puntero a la interfaz de [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) .  
  
 *pColumns*  
 \[out\] Un puntero a la memoria de la que para devolver el número de columnas del conjunto de filas; este número incluye la columna de marcador, si la hay.  
  
 *ppColumnInfo*  
 \[out\] Un puntero a la memoria de la que para devolver una matriz de estructuras de **DBCOLUMNINFO** .  Vea “estructuras de DBCOLUMNINFO” en [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) en *la referencia del*programador.  
  
 `ppStringsBuffer`  
 \[out\] Un puntero a la memoria de la que para devolver un puntero al almacenamiento de todos los valores de cadena \(los nombres utilizó dentro *de columnid* o para *el pwszName*\) dentro de un único bloque de asignación.  
  
## Valor devuelto  
 Uno de los valores estándar de `HRESULT` .  
  
## Comentarios  
 Vea [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) en *la referencia del* programador para obtener información sobre los tipos de datos **DBORDINAL**, **DBCOLUMNINFO**, y **OLECHAR**.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)