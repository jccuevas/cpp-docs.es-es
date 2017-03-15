---
title: "CDataSource (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CDataSource"
  - "ATL::CDataSource"
  - "CDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataSource (clase)"
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CDataSource (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Corresponde al origen de datos OLE DB un objeto, que representa una conexión a través de un proveedor a un origen de datos.  
  
## Sintaxis  
  
```  
class CDataSource  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[Cerrar](../../data/oledb/cdatasource-close.md)|Cierre la conexión.|  
|[GetInitializationString](../../data/oledb/cdatasource-getinitializationstring.md)|Recupera la cadena de inicialización de origen de datos abierto.|  
|[GetProperties](../../data/oledb/cdatasource-getproperties.md)|Obtiene los valores de las propiedades establecidas actualmente para el origen de datos conectado.|  
|[GetProperty](../../data/oledb/cdatasource-getproperty.md)|Obtiene el valor de una propiedad establecida actualmente para el origen de datos conectado.|  
|[Abrir](../../data/oledb/cdatasource-open.md)|Crea una conexión a un proveedor \(origen de datos\) mediante **CLSID**, **Id. de programa**, o un moniker de `CEnumerator` proporcionado por el llamador.|  
|[OpenFromFileName](../../data/oledb/cdatasource-openfromfilename.md)|Abra un origen de datos de un archivo especificado por el nombre de archivo usuario\- proporcionado.|  
|[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)|Abra el origen de datos especificado por una cadena de inicialización.|  
|[OpenWithPromptFileName](../../data/oledb/cdatasource-openwithpromptfilename.md)|Permite al usuario seleccionar un archivo creado previamente de vínculo de datos para abrir el origen de datos correspondiente.|  
|[OpenWithServiceComponents](../../data/oledb/cdatasource-openwithservicecomponents.md)|Abra un objeto de origen de datos mediante el cuadro de diálogo de vínculo de datos.|  
  
## Comentarios  
 Una o varias sesiones de la base de datos se pueden crear para una sola conexión.  `CSession`representan a estas sesiones.  Debe llamar a [CDataSource::Open](../../data/oledb/cdatasource-open.md) para abrir la conexión antes de crear una sesión con `CSession::Open`.  
  
 Para obtener un ejemplo de cómo utilizar `CDataSource`, vea el ejemplo de [CatDB](../../top/visual-cpp-samples.md) .  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)