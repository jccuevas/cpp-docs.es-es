---
title: "CNoRowset (Clase) | Microsoft Docs"
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
  - "ATL.CNoRowset"
  - "ATL::CNoRowset<TAccessor>"
  - "CNoRowset"
  - "ATL.CNoRowset<TAccessor>"
  - "ATL::CNoRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNoRowset (clase)"
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CNoRowset (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se puede utilizar como argumento de plantilla \(`TRowset`\) para [CCommand](../../data/oledb/ccommand-class.md) o [CTable](../../data/oledb/ctable-class.md).  
  
## Sintaxis  
  
```  
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
#### Parámetros  
 `TAccessor`  
 Una clase de descriptor de acceso.  El valor predeterminado es `CAccessorBase`.  
  
## Comentarios  
 Utilice `CNoRowset` como argumento de plantilla si el comando no devuelve un conjunto de filas.  
  
 `CNoRowset` implementa los siguientes métodos de código auxiliar, que corresponden a otros métodos de clase de descriptor de acceso:  
  
-   **BindFinished** \- Indica cuando se completa el enlace \(devuelve `S_OK`\).  
  
-   **cerrar** \- Filas de versiones y la interfaz actual IRowset.  
  
-   `GetIID` \- recupera el identificador de interfaz de un punto de conexión.  
  
-   **GetInterface** \- recupera una interfaz.  
  
-   `GetInterfacePtr` \- recupera un puntero encapsulado de interfaz.  
  
-   **SetAccessor** \- establece un puntero al descriptor de acceso.  
  
-   **SetupOptionalRowsetInterfaces** \- interfaces opcionales de conjuntos \- hacia arriba para el conjunto de filas.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)