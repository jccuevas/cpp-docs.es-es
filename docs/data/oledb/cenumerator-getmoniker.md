---
title: "CEnumerator::GetMoniker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetMoniker"
  - "CEnumerator.GetMoniker"
  - "CEnumerator::GetMoniker"
  - "ATL.CEnumerator.GetMoniker"
  - "ATL::CEnumerator::GetMoniker"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetMoniker (método)"
ms.assetid: 69a5cf2d-4a94-41dc-812d-bc1661d516d2
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CEnumerator::GetMoniker
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Analiza el nombre para mostrar para extraer el componente de la cadena que se puede convertir en un moniker.  
  
## Sintaxis  
  
```  
  
      HRESULT GetMoniker(   
   LPMONIKER* ppMoniker    
) const throw( );  
HRESULT GetMoniker(   
   LPMONIKER* ppMoniker,   
   LPCTSTR lpszDisplayName    
) const throw( );  
```  
  
#### Parámetros  
 *ppMoniker*  
 \[out\] El moniker analizado del nombre para mostrar \([CEnumeratorAccessor::m\_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)\) de la fila actual.  
  
 *lpszDisplayName*  
 \[in\] El nombre para mostrar a analizar.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CEnumerator \(Clase\)](../../data/oledb/cenumerator-class.md)