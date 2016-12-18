---
title: "CRowset::GetApproximatePosition | Microsoft Docs"
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
  - "ATL::CRowset::GetApproximatePosition"
  - "ATL::CRowset<TAccessor>::GetApproximatePosition"
  - "CRowset.GetApproximatePosition"
  - "CRowset::GetApproximatePosition"
  - "GetApproximatePosition"
  - "ATL.CRowset.GetApproximatePosition"
  - "CRowset<TAccessor>::GetApproximatePosition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetApproximatePosition (método)"
ms.assetid: 8f9ccd41-0590-468e-b202-6731d0f99d21
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::GetApproximatePosition
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve la posición aproximada de una fila correspondiente a un marcador.  
  
## Sintaxis  
  
```  
  
      HRESULT GetApproximatePosition(   
   const CBookmarkBase* pBookmark,   
   DBCOUNTITEM* pPosition,   
   DBCOUNTITEM* pcRows    
) throw( );  
```  
  
#### Parámetros  
 `pBookmark`  
 \[in\] Un puntero a un marcador que identifica la fila cuya posición es encontrar.  **nulo** si se requiere el recuento de filas.  
  
 *pPosition*  
 \[out\] Un puntero a la ubicación donde `GetApproximatePosition` devuelve la posición de la fila.  **nulo** si la posición no se requiere.  
  
 `pcRows`  
 \[out\] Un puntero a la ubicación donde `GetApproximatePosition` devuelve el número total de filas.  **nulo** si el recuento de filas no se requiere.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método requiere la interfaz opcional `IRowsetScroll`, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetScroll** a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
 Para obtener información sobre cómo utilizar marca una dirección de la Internet en consumidores, vea [Mediante los marcadores](../../data/oledb/using-bookmarks.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [IRowsetScroll::GetApproximatePosition](https://msdn.microsoft.com/en-us/library/ms712901.aspx)