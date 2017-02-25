---
title: "CEnumerator::Open | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CEnumerator.Open"
  - "CEnumerator::Open"
  - "ATL::CEnumerator::Open"
  - "CEnumerator.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open (método)"
ms.assetid: b22821a0-257a-4543-ad0c-2649d4ac092e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CEnumerator::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Enlaza el moniker del enumerador, si se especifica uno, entonces recupera el conjunto de filas para el enumerador llamando a [ISourcesRowset::GetSourcesRowset](https://msdn.microsoft.com/en-us/library/ms711200.aspx).  
  
## Sintaxis  
  
```  
  
      HRESULT Open(   
   LPMONIKER pMoniker    
) throw( );  
HRESULT Open(   
   const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR    
) throw( );  
HRESULT Open(   
   const CEnumerator& enumerator    
) throw( );  
```  
  
#### Parámetros  
 `pMoniker`  
 \[in\] Un puntero a un moniker para un enumerador.  
  
 *pClsid*  
 \[in\] Un puntero a **CLSID** de un enumerador.  
  
 `enumerator`  
 \[in\] Una referencia a un enumerador.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CEnumerator \(Clase\)](../../data/oledb/cenumerator-class.md)