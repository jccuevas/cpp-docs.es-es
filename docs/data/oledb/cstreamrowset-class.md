---
title: "CStreamRowset (Clase) | Microsoft Docs"
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
  - "ATL::CStreamRowset<TAccessor>"
  - "ATL::CStreamRowset"
  - "CStreamRowset"
  - "ATL.CStreamRowset<TAccessor>"
  - "ATL.CStreamRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStreamRowset (clase)"
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStreamRowset (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza en una declaración de `CCommand` o de `CTable` .  
  
## Sintaxis  
  
```  
template <class TAccessor = CAccessorBase>  
class CStreamRowset  
```  
  
#### Parámetros  
 `TAccessor`  
 Una clase de descriptor de acceso.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[CStreamRowset](../../data/oledb/cstreamrowset-cstreamrowset.md)|Constructor.  Crea instancias e inicializa el objeto de `CStreamRowset` .|  
|[Cerrar](../../data/oledb/cstreamrowset-close.md)|Libera el puntero de interfaz de [ISequentialStream](https://msdn.microsoft.com/en-us/library/ms718035.aspx) en la clase.|  
  
## Comentarios  
 Utilice `CStreamRowset` en la declaración de `CCommand` o de `CTable` , por ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/CPP/cstreamrowset-class_1.cpp)]  
  
 \-O bien\-  
  
 [!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/CPP/cstreamrowset-class_2.cpp)]  
  
 `ICommand::Execute` devuelve un puntero de `ISequentialStream` , que se almacena en `m_spStream`.  Se utiliza el método de **de lectura** para recuperar los datos \(de la cadena XML.  Por ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/CPP/cstreamrowset-class_3.cpp)]  
  
 SQL Server 2000 aplica el formato XML, y devolverá todas las columnas y filas del conjunto de filas como una cadena XML.  
  
> [!NOTE]
>  Esta característica sólo funciona con SQL Server 2000.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)