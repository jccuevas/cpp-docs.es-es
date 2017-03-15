---
title: "AtlTraceErrorRecords | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.AtlTraceErrorRecords"
  - "ATL::AtlTraceErrorRecords"
  - "AtlTraceErrorRecords"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AtlTraceErrorRecords (función)"
ms.assetid: b83970b3-dc2a-445c-9142-f52218719905
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# AtlTraceErrorRecords
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Vuelca información de registro de errores de OLE DB al dispositivo de volcado si se devuelve un error.  
  
## Sintaxis  
  
```  
  
      inline void AtlTraceErrorRecords(   
   HRESULT hrErr = S_OK    
);  
```  
  
#### Parámetros  
 `hErr`  
 \[in\] `HRESULT` devuelto por una función miembro para plantillas de consumidor OLE DB.  
  
## Comentarios  
 Si `hErr` no es `S_OK`, `AtlTraceErrorRecords` vuelca información de registro de errores de OLE DB al dispositivo de volcado \(la ficha de **debug** de la ventana de resultados o de un archivo\).  La información de registro de errores, que se obtiene del proveedor, incluye el número de fila, el origen, la descripción, el archivo de ayuda, el contexto, y GUID para cada entrada de registro de errores.  `AtlTraceErrorRecords` vuelca esta información sólo en versiones de depuración.  En las versiones de lanzamiento, es un código auxiliar vacío que se optimiza out.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [CDBErrorInfo \(Clase\)](../../data/oledb/cdberrorinfo-class.md)