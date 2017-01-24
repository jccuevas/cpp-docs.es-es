---
title: "CRowset::GetDataHere | Microsoft Docs"
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
  - "CRowset<TAccessor>::GetDataHere"
  - "CRowset<TAccessor>.GetDataHere"
  - "CRowset.GetDataHere"
  - "GetDataHere"
  - "CRowset::GetDataHere"
  - "ATL::CRowset::GetDataHere"
  - "ATL::CRowset<TAccessor>::GetDataHere"
  - "ATL.CRowset<TAccessor>.GetDataHere"
  - "ATL.CRowset.GetDataHere"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetDataHere (método)"
ms.assetid: 2fe2a987-1c4c-4299-876e-0591caf63af4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::GetDataHere
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera datos de la fila y los lugares actuales él en el búfer especificado.  
  
## Sintaxis  
  
```  
  
      HRESULT GetDataHere(   
   int nAccessor,   
   void* pBuffer    
) throw( );  
```  
  
#### Parámetros  
 `nAccessor`  
 \[in\] El número de índice de descriptor de acceso para tener acceso a los datos.  
  
 `pBuffer`  
 \[out\] Un búfer en el que colocar los datos del registro actual.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Para obtener un ejemplo de cómo utilizar esta función, vea [Ejemplo MultiRead](../../top/visual-cpp-samples.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [CRowset::GetData](../../data/oledb/crowset-getdata.md)