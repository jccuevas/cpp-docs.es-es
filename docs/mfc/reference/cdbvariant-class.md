---
title: "CDBVariant Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDBVariant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBVariant (clase)"
  - "Variant (tipos de datos), ODBC"
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CDBVariant Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un tipo de datos variant para las clases ODBC de MFC.  
  
## Sintaxis  
  
```  
class CDBVariant  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDBVariant::CDBVariant](../Topic/CDBVariant::CDBVariant.md)|Crea un objeto `CDBVariant`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDBVariant::Clear](../Topic/CDBVariant::Clear.md)|borra el objeto de `CDBVariant` .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDBVariant::m\_dwType](../Topic/CDBVariant::m_dwType.md)|Contiene el tipo de datos del valor actualmente almacenado.  Escriba `DWORD`.|  
  
### Unión públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDBVariant::m\_boolVal](../Topic/CDBVariant::m_boolVal.md)|contiene un valor de **BOOL**escrito.|  
|[CDBVariant::m\_chVal](../Topic/CDBVariant::m_chVal.md)|contiene un valor de `unsigned char`escrito.|  
|[CDBVariant::m\_dblVal](../Topic/CDBVariant::m_dblVal.md)|contiene un valor de **Doble**escrito.|  
|[CDBVariant::m\_fltVal](../Topic/CDBVariant::m_fltVal.md)|contiene un valor de **Hacer flotante**escrito.|  
|[CDBVariant::m\_iVal](../Topic/CDBVariant::m_iVal.md)|contiene un valor de **Corto**escrito.|  
|[CDBVariant::m\_lVal](../Topic/CDBVariant::m_lVal.md)|contiene un valor de **Más**escrito.|  
|[CDBVariant::m\_pbinary](../Topic/CDBVariant::m_pbinary.md)|contiene un puntero a un objeto de `CLongBinary`escrito.|  
|[CDBVariant::m\_pdate](../Topic/CDBVariant::m_pdate.md)|contiene un puntero a un objeto de **TIMESTAMP\_STRUCT**escrito.|  
|[CDBVariant::m\_pstring](../Topic/CDBVariant::m_pstring.md)|contiene un puntero a un objeto de `CString`escrito.|  
|[CDBVariant::m\_pstringA](../Topic/CDBVariant::m_pstringA.md)|almacena un puntero a un objeto ASCII de [CString](../../atl-mfc-shared/reference/cstringt-class.md) .|  
|[CDBVariant::m\_pstringW](../Topic/CDBVariant::m_pstringW.md)|almacena un puntero a un objeto ancho de [CString](../../atl-mfc-shared/reference/cstringt-class.md) .|  
  
## Comentarios  
 `CDBVariant` no tiene una clase base.  
  
 `CDBVariant` es similar a [COleVariant](../../mfc/reference/colevariant-class.md); sin embargo, `CDBVariant` no utiliza OLE.  `CDBVariant` permite almacenar un valor sin preocuparse de tipo de datos del valor.  `CDBVariant` sigue el tipo de datos del valor actual, que se almacena en una combinación.  
  
 La clase [CRecordset](../../mfc/reference/crecordset-class.md) usa objetos de `CDBVariant` en funciones con tres miembros: `GetFieldValue`, `GetBookmark`, y `SetBookmark`.  Por ejemplo, `GetFieldValue` permite capturar datos dinámicamente en una columna.  Dado que el tipo de datos de la columna puede no ser conocido en tiempo de ejecución, `GetFieldValue` usa un objeto de `CDBVariant` para almacenar los datos de la columna.  
  
## Jerarquía de herencia  
 `CDBVariant`  
  
## Requisitos  
 **encabezado:** afxdb.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CRecordset::GetFieldValue](../Topic/CRecordset::GetFieldValue.md)   
 [CRecordset::GetBookmark](../Topic/CRecordset::GetBookmark.md)   
 [CRecordset::SetBookmark](../Topic/CRecordset::SetBookmark.md)