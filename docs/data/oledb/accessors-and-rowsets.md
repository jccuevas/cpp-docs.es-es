---
title: "Descriptores de acceso y conjuntos de filas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "descriptores de acceso [C++]"
  - "descriptores de acceso [C++], conjuntos de filas"
  - "conjuntos de filas de matriz"
  - "conjuntos de filas masivos"
  - "CAccessorBase (clase)"
  - "CAccessorRowset (clase), tipos de descriptores de acceso"
  - "CArrayRowset (clase), descriptores de acceso"
  - "CBulkRowset (clase), descriptores de acceso"
  - "CRowset (clase), descriptores de acceso y conjuntos de fila"
  - "plantillas de consumidor OLE DB, descriptores de acceso"
  - "plantillas de consumidor OLE DB, compatibilidad con los conjuntos de filas"
  - "conjuntos de filas [C++], obtener acceso"
  - "conjuntos de filas [C++], tipos compatibles"
  - "conjuntos de filas simples"
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Descriptores de acceso y conjuntos de filas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para establecer y recuperar datos, las plantillas OLE DB usan un descriptor de acceso y un conjunto de filas a través de la clase [CAccessorRowset](../../data/oledb/caccessorrowset-class.md).  Esta clase es capaz de controlar múltiples descriptores de acceso de varios tipos.  
  
## Tipos de descriptores de acceso  
 Todos los descriptores de acceso se derivan de [CAccessorBase](../../data/oledb/caccessorbase-class.md).  `CAccessorBase` proporciona el enlace del parámetro y la columna.  
  
 La siguiente ilustración muestra los tipos de descriptores de acceso.  
  
 ![Tipos de descriptores de acceso](../../data/oledb/media/vcaccessortypes.png "vcAccessorTypes")  
Clases de descriptores de acceso  
  
-   [CAccessor](../../data/oledb/caccessor-class.md) Use este descriptor de acceso si conoce la estructura del origen de la base de datos en tiempo de diseño.  `CAccessor` enlaza estáticamente un registro de base de datos, que contiene el búfer, al origen de datos.  
  
-   [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) Use este descriptor de acceso si no conoce la estructura del origen de la base de datos en tiempo de diseño.  `CDynamicAccessor` llama a `IColumnsInfo::GetColumnInfo` para obtener la información de columna de base de datos.  Crea y administra un descriptor de acceso y el búfer.  
  
-   [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) Use este descriptor de acceso para controlar tipos de comando desconocidos.  Al preparar los comandos, `CDynamicParameterAccessor` puede obtener información de parámetros de la interfaz `ICommandWithParameters` si el proveedor la admite.  
  
-   [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md), [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md) y [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md) Use estas clases si no tiene ningún conocimiento del esquema de base de datos.  `CDynamicStringAccessorA` recupera los datos como cadenas ANSI; `CDynamicStringAccessorW` recupera los datos como cadenas Unicode.  
  
-   [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) Con esta clase se pueden utilizar los tipos de datos que se deseen si el proveedor es capaz de convertir el tipo.  Controla tanto columnas de resultados como parámetros de comando.  
  
 A continuación se muestra la lista de compatibilidades de los descriptores de acceso de las plantillas OLE DB.  
  
|Tipo de descriptor de acceso|Dinámico|Controla parámetros|Búfer|Múltiples descriptores de acceso|  
|----------------------------------|--------------|-------------------------|-----------|--------------------------------------|  
|`CAccessor`|No|Sí|Usuario|Sí|  
|`CDynamicAccessor`|Sí|No|Plantillas OLE DB|No|  
|`CDynamicParameterAccessor`|Sí|Sí|Plantillas OLE DB|No|  
|`CDynamicStringAccessor[A,W]`|Sí|No|Plantillas OLE DB|No|  
|`CManualAccessor`|Sí|Sí|Usuario|Sí|  
  
## Tipos de conjuntos de filas  
 Las plantillas OLE DB admiten tres tipos de conjuntos de filas \(vea la ilustración anterior\): conjuntos de filas simples \(implementados por [CRowset](../../data/oledb/crowset-class.md)\), conjuntos de filas masivos \(implementados por [CBulkRowset](../../data/oledb/cbulkrowset-class.md)\) y conjuntos de filas de matriz \(implementados por [CArrayRowset](../../data/oledb/carrayrowset-class.md)\).  Los conjuntos de filas simples recuperan un único identificador de fila cuando se llama a `MoveNext`.  Los conjuntos de filas masivos pueden recuperar múltiples identificadores de fila.  Los conjuntos de filas de matriz son conjuntos de filas a los que se puede tener acceso por medio de la sintaxis de matrices.  
  
 La siguiente ilustración muestra los tipos de conjuntos de filas.  
  
 ![Gráfico RowsetType](../../data/oledb/media/vcrowsettypes.png "vcRowsetTypes")  
Clases de conjuntos de filas  
  
 [Los conjuntos de filas de esquema](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) no obtienen acceso a los datos del almacén de datos, pero sí a la información acerca de éste, denominada metadatos.  Los conjuntos de filas de esquema se usan normalmente en situaciones en las que no se conoce la estructura de la base de datos en tiempo de compilación y es necesario obtenerla en tiempo de ejecución.  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)