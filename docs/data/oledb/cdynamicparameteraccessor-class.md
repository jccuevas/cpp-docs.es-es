---
title: "CDynamicParameterAccessor (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CDynamicParameterAccessor"
  - "ATL::CDynamicParameterAccessor"
  - "CDynamicParameterAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicParameterAccessor (clase)"
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CDynamicParameterAccessor (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Similar a [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), pero obtiene la información de parámetros que se va a establecer llamando a la interfaz [ICommandWithParameters](https://msdn.microsoft.com/en-us/library/ms712937.aspx).  
  
## Sintaxis  
  
```  
class CDynamicParameterAccessor : public CDynamicAccessor  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-cdynamicparameteraccessor.md)|El constructor.|  
|[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)|Recupera los datos de parámetros del búfer.|  
|[GetParamCount](../../data/oledb/cdynamicparameteraccessor-getparamcount.md)|Recupera el número de parámetros en el descriptor de acceso.|  
|[GetParamIO](../../data/oledb/cdynamicparameteraccessor-getparamio.md)|Determina si el parámetro especificado es un parámetro de entrada o salida.|  
|[GetParamLength](../../data/oledb/cdynamicparameteraccessor-getparamlength.md)|Recupera la longitud del parámetro especificado almacenado en el búfer.|  
|[GetParamName](../../data/oledb/cdynamicparameteraccessor-getparamname.md)|Recupera el nombre de un parámetro especificado.|  
|[GetParamStatus](../../data/oledb/cdynamicparameteraccessor-getparamstatus.md)|Recupera el estado del parámetro especificado almacenado en el búfer.|  
|[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)|Recupera los datos de cadena del parámetro especificado almacenado en el búfer.|  
|[GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)|Recupera el tipo de datos de un parámetro especificado.|  
|[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)|Establece el búfer con los datos de parámetros.|  
|[SetParamLength](../../data/oledb/cdynamicparameteraccessor-setparamlength.md)|Establece la longitud del parámetro especificado almacenado en el búfer.|  
|[SetParamStatus](../../data/oledb/cdynamicparameteraccessor-setparamstatus.md)|Establece el estado del parámetro especificado almacenado en el búfer.|  
|[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)|Establece los datos de cadena del parámetro especificado almacenado en el búfer.|  
  
## Comentarios  
 El proveedor debe admitir `ICommandWithParameters` para que el consumidor pueda usar esta clase.  
  
 La información de parámetros se almacena en un búfer creado y administrado por esta clase. Obtenga los datos de parámetros que están en el búfer mediante [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) y [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).  
  
 Para ver un ejemplo que muestra cómo usar esta clase para ejecutar un procedimiento almacenado de SQL Server y obtener los valores de parámetros de salida, consulte el artículo de Knowledge Base Q058860, "HOWTO: Execute Stored Procedure using CDynamicParameterAccessor". Los artículos de Knowledge Base están disponibles en la documentación de Visual Studio de MSDN Library o en [http:\/\/support.microsoft.com\/](http://support.microsoft.com).  
  
## Requisitos  
 **Encabezado**: atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor \(Clase\)](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)   
 [CManualAccessor \(Clase\)](../../data/oledb/cmanualaccessor-class.md)