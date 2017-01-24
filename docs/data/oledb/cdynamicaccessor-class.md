---
title: "CDynamicAccessor (Clase) | Microsoft Docs"
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
  - "ATL.CDynamicAccessor"
  - "ATL::CDynamicAccessor"
  - "CDynamicAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicAccessor (clase)"
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite obtener acceso a un origen de datos cuando no se conoce el esquema de base de datos \(la estructura subyacente de la base de datos\).  
  
## Sintaxis  
  
```  
class CDynamicAccessor : public CAccessorBase  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cdynamicaccessor-addbindentry.md)|Agrega una entrada de enlace a las columnas de salida al reemplazar el descriptor de acceso predeterminado.|  
|[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)|Crea instancias e inicializa el objeto de `CDynamicAccessor` .|  
|[Cerrar](../../data/oledb/cdynamicaccessor-close.md)|Desata todas las columnas, libera la memoria asignada, y libera el puntero de interfaz de [IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) en la clase.|  
|[GetBookmark](../../data/oledb/cdynamicaccessor-getbookmark.md)|Recupera el marcador para la fila actual.|  
|[GetBlobHandling](../../data/oledb/cdynamicaccessor-getblobhandling.md)|Recupera BLOB que administra el valor de la fila actual.|  
|[GetBlobSizeLimit](../../data/oledb/cdynamicaccessor-getblobsizelimit.md)|Recupera el tamaño máximo del BLOB en bytes.|  
|[GetColumnCount](../../data/oledb/cdynamicaccessor-getcolumncount.md)|Recupera el número de columnas del conjunto de filas.|  
|[GetColumnFlags](../../data/oledb/cdynamicaccessor-getcolumnflags.md)|Recupera las características de la columna.|  
|[GetColumnInfo](../../data/oledb/cdynamicaccessor-getcolumninfo.md)|Recupera los metadatos de columna.|  
|[GetColumnName](../../data/oledb/cdynamicaccessor-getcolumnname.md)|Recupera el nombre de una columna especificada.|  
|[GetColumnType](../../data/oledb/cdynamicaccessor-getcolumntype.md)|Recupera el tipo de datos de una columna especificada.|  
|[GetLength](../../data/oledb/cdynamicaccessor-getlength.md)|Recupera la longitud posible máxima de una columna en bytes.|  
|[GetOrdinal](../../data/oledb/cdynamicaccessor-getordinal.md)|Recupera el índice de columna especificado un nombre de columna.|  
|[GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)|Recupera el estado de una columna especificada.|  
|[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)|Recupera los datos del búfer.|  
|[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)|Establece BLOB que administra el valor de la fila actual.|  
|[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)|Establece el tamaño máximo del BLOB en bytes.|  
|[SetLength](../../data/oledb/cdynamicaccessor-setlength.md)|Establece la longitud de la columna en bytes.|  
|[SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)|Establece el estado de una columna especificada.|  
|[SetValue](../../data/oledb/cdynamicaccessor-setvalue.md)|Almacena los datos en el búfer.|  
  
## Comentarios  
 Utilice los métodos de `CDynamicAccessor` para obtener información como nombres de columna, recuento de columna, tipo de datos de la columna, y así sucesivamente.  Se utiliza esta información de columna para crear un descriptor de acceso dinámicamente en tiempo de ejecución.  
  
 La información de columnas se almacena en un búfer creado y administrado por esta clase.  Obtenga los datos del búfer a [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).  
  
 Para obtener una descripción y ejemplos del uso de las clases de descriptor de acceso, vea [Utilizar descriptores de acceso dinámicos](../../data/oledb/using-dynamic-accessors.md).  
  
## Requisitos  
 **Encabezado**: atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor \(Clase\)](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor \(Clase\)](../../data/oledb/cmanualaccessor-class.md)