---
title: "CXMLAccessor (Clase) | Microsoft Docs"
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
  - "ATL::CXMLAccessor"
  - "CXMLAccessor"
  - "ATL.CXMLAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CXMLAccessor (clase)"
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CXMLAccessor (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite obtener acceso a orígenes de datos como datos de cadena cuando no se conoce el esquema del almacén de datos \(estructura subyacente\).  
  
## Sintaxis  
  
```  
class CXMLAccessor : public CDynamicStringAccessorW  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)|Recupera la información de columna.|  
|[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)|Recupera el contenido completo de una tabla por filas.|  
  
## Comentarios  
 Sin embargo, `CXMLAccessor` diferencia de `CDynamicStringAccessorW` en que convierte todos los datos acceso de almacén como datos \(etiquetados\) XML\- con formato.  Esto es especialmente útil para la salida de las páginas Web XML\- con conocimiento pleno.  Los nombres de etiqueta XML con los nombres de columna del almacén de datos lo más posible.  
  
 Para obtener información de columnas, utilice métodos `CDynamicAccessor`.  Utilice esta información de columna para crear un descriptor de acceso dinámicamente en tiempo de ejecución.  
  
 La información de columnas se almacena en un búfer creado y administrado por esta clase.  Obtener información de columna mediante [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) u obtener los datos de columna por filas mediante [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md).  
  
## Ejemplo  
 [!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/CPP/cxmlaccessor-class_1.cpp)]  
  
## Requisitos  
 **Encabezado**: atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor \(Clase\)](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CDynamicStringAccessor \(Clase\)](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicStringAccessorA \(Clase\)](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW \(Clase\)](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CManualAccessor \(Clase\)](../../data/oledb/cmanualaccessor-class.md)