---
title: "CXMLAccessor::GetXMLColumnData | Microsoft Docs"
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
  - "ATL.CXMLAccessor.GetXMLColumnData"
  - "CXMLAccessor::GetXMLColumnData"
  - "CXMLAccessor.GetXMLColumnData"
  - "ATL::CXMLAccessor::GetXMLColumnData"
  - "GetXMLColumnData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetXMLColumnData (método)"
ms.assetid: 719e8efe-8758-4af7-a855-0e44ea196546
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CXMLAccessor::GetXMLColumnData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera información del tipo de columna de una tabla como datos XML\- con formato de cadena, por columna.  
  
## Sintaxis  
  
```  
  
      HRESULT GetXMLColumnData(   
   CSimpleStringW& strOutput    
) throw( );  
```  
  
#### Parámetros  
 `strOutput`  
 \[out\] Una referencia a un búfer de cadena que contiene la información del tipo de columna que se va a recuperar.  La cadena se le da formato con los nombres de etiqueta XML que coinciden con los nombres de columna del almacén de datos.  
  
## Valor devuelto  
 Uno de los valores estándar de `HRESULT` .  
  
## Comentarios  
 A continuación se muestra cómo la información del tipo de columna se da formato en XML.  `type` especifica el tipo de datos de la columna.  Observe que los tipos de datos se basan en los tipos de datos OLE DB, no los de la base de datos que se logra.  
  
 `<columninfo>`  
  
 `<column type = I2/> ColumnName`  
  
 `</columninfo>`  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CXMLAccessor \(Clase\)](../../data/oledb/cxmlaccessor-class.md)