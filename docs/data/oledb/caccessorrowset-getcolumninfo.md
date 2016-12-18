---
title: "CAccessorRowset::GetColumnInfo | Microsoft Docs"
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
  - "CAccessorRowset.GetColumnInfo"
  - "CAccessorRowset::GetColumnInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnInfo (método)"
ms.assetid: 8ade2388-3c58-43cd-8ed6-499ee0531291
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorRowset::GetColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la información de la columna de conjunto de filas abierto.  
  
## Sintaxis  
  
```  
  
      HRESULT GetColumnInfo(  
   DBORDINAL* pulColumns,  
   DBCOLUMNINFO** ppColumnInfo,  
   LPOLESTR* ppStrings   
) const;  
HRESULT GetColumnInfo(  
   DBORDINAL* pColumns,  
   DBCOLUMNINFO** ppColumnInfo   
);  
```  
  
#### Parámetros  
 Vea [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) en *la referencia del*programador.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 El usuario debe liberar la información y el búfer de cadena devueltos de la columna.  Utilice la segunda versión de este método cuando se utiliza [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) y necesita reemplazar los enlaces.  
  
 Para obtener más información, vea [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CAccessorRowset \(Clase\)](../../data/oledb/caccessorrowset-class.md)