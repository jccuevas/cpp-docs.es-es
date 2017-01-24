---
title: "CXMLAccessor::GetXMLRowData | Microsoft Docs"
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
  - "ATL::CXMLAccessor::GetXMLRowData"
  - "ATL.CXMLAccessor.GetXMLRowData"
  - "CXMLAccessor::GetXMLRowData"
  - "CXMLAccessor.GetXMLRowData"
  - "GetXMLRowData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetXMLRowData (método)"
ms.assetid: 156b66e3-42fd-491c-8943-38cf5e36f687
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CXMLAccessor::GetXMLRowData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el contenido completo de una tabla como datos XML\- con formato de cadena, fila por fila.  
  
## Sintaxis  
  
```  
  
      HRESULT GetXMLRowData(   
   CSimpleStringW& strOutput,   
   bool bAppend = false    
) throw( );  
```  
  
#### Parámetros  
 `strOutput`  
 \[out\] Una referencia a un búfer que contiene los datos de la tabla que se recuperarán.  Los datos se da formato como datos de cadena con los nombres de etiqueta XML que coinciden con los nombres de columna del almacén de datos.  
  
 *bAppend*  
 \[in\] Valor booleano que especifica si anexar una cadena al final de los datos de salida.  
  
## Valor devuelto  
 Uno de los valores estándar de `HRESULT` .  
  
## Comentarios  
 A continuación se muestra cómo los datos de la fila se da formato en XML.  `DATA` siguiente representa los datos de la fila.  Utilice métodos de movimiento para desplazarse a la fila deseada.  
  
 `<row>`  
  
 `<column name>DATA</column name>`  
  
 `</row>`  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CXMLAccessor \(Clase\)](../../data/oledb/cxmlaccessor-class.md)