---
title: "CBulkRowset::MoveToRatio | Microsoft Docs"
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
  - "CBulkRowset.MoveToRatio"
  - "ATL::CBulkRowset::MoveToRatio"
  - "MoveToRatio"
  - "CBulkRowset::MoveToRatio"
  - "ATL.CBulkRowset<TAccessor>.MoveToRatio"
  - "ATL::CBulkRowset<TAccessor>::MoveToRatio"
  - "ATL.CBulkRowset.MoveToRatio"
  - "CBulkRowset<TAccessor>::MoveToRatio"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToRatio (método)"
ms.assetid: 86be60f5-9341-44c1-8e1e-9174c082d0d5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBulkRowset::MoveToRatio
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Captura filas de una posición fraccionarios en el conjunto de filas.  
  
## Sintaxis  
  
```  
  
      HRESULT MoveToRatio(  
   DBCOUNTITEM nNumerator,  
   DBCOUNTITEM nDenominator   
) throw( );  
```  
  
#### Parámetros  
 `nNumerator`  
 \[in\] El numerador utilizado para determinar la posición fraccionaria de la que para capturar datos.  
  
 `nDenominator`  
 \[in\] El denominador utilizado para determinar la posición fraccionaria de la que para capturar datos.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 `MoveToRatio` captura las filas aproximadamente según la siguiente fórmula:  
  
 `( nNumerator *  RowsetSize ) / nDenominator`  
  
 Donde es el tamaño `RowsetSize` de conjunto de filas, medido en filas.  La exactitud de esta fórmula depende del proveedor específico.  Para obtener información detallada, vea [IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CBulkRowset \(Clase\)](../../data/oledb/cbulkrowset-class.md)