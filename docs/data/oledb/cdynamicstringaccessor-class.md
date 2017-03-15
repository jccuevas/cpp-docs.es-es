---
title: "CDynamicStringAccessor (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicStringAccessor (clase)"
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CDynamicStringAccessor (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite obtener acceso a un origen de datos cuando no se conoce el esquema de base de datos \(la estructura subyacente de la base de datos\).  
  
## Sintaxis  
  
```  
  
      template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)|Recupera los datos de columna especificados como cadena.|  
|[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)|Establece los datos de columna especificados como cadena.|  
  
## Comentarios  
 Mientras [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) solicita datos en formato nativo compatible con el proveedor, las solicitudes de `CDynamicStringAccessor` que el proveedor que todos los datos se obtiene acceso desde el almacén de datos como datos de cadena.  Esto es de especial utilidad para tareas sencillas que no requieren el cálculo de valores en el almacén de datos, como mostrar o imprimir su contenido.  
  
 El tipo nativo de datos de columna en el almacén de datos independientemente; siempre que el proveedor admita la conversión de datos, proporcionará los datos en formato de cadena.  Si el proveedor no admite la conversión del tipo de datos nativo a una cadena \(que no es común\), la llamada que solicita devolverá el valor correcto **DB\_S\_ERRORSOCCURED**, y el estado de la columna correspondiente indicará un problema de conversión con **DBSTATUS\_E\_CANTCONVERTVALUE**.  
  
 Para obtener información de columnas, utilice métodos `CDynamicStringAccessor`.  Utilice esta información de columna para crear un descriptor de acceso dinámicamente en tiempo de ejecución.  
  
 La información de columnas se almacena en un búfer creado y administrado por esta clase.  Obtenga los datos del búfer a [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md), o almacénelos en el búfer mediante [SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).  
  
 Para obtener una descripción y ejemplos del uso de las clases de descriptor de acceso, vea [Utilizar descriptores de acceso dinámicos](../../data/oledb/using-dynamic-accessors.md).  
  
## Requisitos  
 **Encabezado**: atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor \(Clase\)](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor \(Clase\)](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessorA \(Clase\)](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW \(Clase\)](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CXMLAccessor \(Clase\)](../../data/oledb/cxmlaccessor-class.md)