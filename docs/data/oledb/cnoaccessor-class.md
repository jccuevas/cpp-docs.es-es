---
title: "CNoAccessor (Clase) | Microsoft Docs"
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
  - "ATL::CNoAccessor"
  - "CNoAccessor"
  - "ATL.CNoAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNoAccessor (clase)"
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CNoAccessor (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se puede utilizar como argumento de plantilla \(`TAccessor`\) para las clases de plantilla, como `CCommand` y `CTable`, que requieren un argumento de la clase de descriptor de acceso.  
  
## Sintaxis  
  
```  
class CNoAccessor  
```  
  
## Comentarios  
 Utilice `CNoAccessor` como argumento de plantilla cuando no desea la clase para admitir parámetros o generar columnas.  
  
 `CNoAccessor` implementa los siguientes métodos de código auxiliar, que corresponden a otros métodos de clase de descriptor de acceso:  
  
-   **BindColumns** \- enlaza las columnas a los descriptores de acceso.  
  
-   `BindParameters` \- enlaza los parámetros creados a las columnas.  
  
-   **Bind** \- crea enlaces.  
  
-   **cerrar** \- Cierra el descriptor de acceso.  
  
-   `ReleaseAccessors` \- libera los descriptores de acceso creados por la clase.  
  
-   `FreeRecordMemory` \- libera cualquier columna del registro actual que necesita ser liberado.  
  
-   `GetColumnInfo` \- obtiene la información de la columna de conjunto de filas abierto.  
  
-   `GetNumAccessors` \- recupera el número de descriptores de acceso creados por la clase.  
  
-   `IsAutoAccessor` \- devuelve true si los datos se recupera automáticamente para el descriptor de acceso durante una operación de movimiento.  
  
-   `GetHAccessor` \- recupera el identificador de descriptor de acceso de un descriptor de acceso especificado.  
  
-   `GetBuffer` \- recupera el puntero al búfer del marcador.  
  
-   **NoBindOnNullRowset** \- evita el enlace de datos en conjuntos de filas vacíos.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)