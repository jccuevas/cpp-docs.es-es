---
title: "CRowset::MoveToRatio | Microsoft Docs"
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
  - "MoveToRatio"
  - "CRowset<TAccessor>::MoveToRatio"
  - "CRowset::MoveToRatio"
  - "CRowset<TAccessor>.MoveToRatio"
  - "ATL.CRowset.MoveToRatio"
  - "ATL::CRowset::MoveToRatio"
  - "CRowset.MoveToRatio"
  - "ATL.CRowset<TAccessor>.MoveToRatio"
  - "ATL::CRowset<TAccessor>::MoveToRatio"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToRatio (método)"
ms.assetid: 1fa313bd-8fd1-4608-8e85-44993b97dd88
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::MoveToRatio
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Captura filas de una posición fraccionarios en el conjunto de filas.  
  
## Sintaxis  
  
```  
  
      HRESULT MoveToRatio(   
   DBCOUNTITEM nNumerator,   
   DBCOUNTITEM nDenominator,   
   bool bForward = true    
) throw( );  
```  
  
#### Parámetros  
 `nNumerator`  
 \[in\] El numerador utilizado para determinar el posicional fraccionario de qué para capturar datos.  
  
 `nDenominator`  
 \[in\] El denominador utilizado para determinar el posicional fraccionario de qué para capturar datos.  
  
 `bForward`  
 \[in\] Indica si avanzar o retroceder.  El valor predeterminado es frontal.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 `MoveToRatio` captura las filas que acuerdan aproximadamente a la siguiente fórmula:  
  
 `( nNumerator *  RowsetSize ) / nDenominator`  
  
 donde es el tamaño `RowsetSize` de conjunto de filas, medido en filas.  La exactitud de esta fórmula depende del proveedor específico.  Para obtener información detallada, vea [IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx).  
  
 Este método requiere la interfaz opcional `IRowsetScroll`, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetScroll** a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)