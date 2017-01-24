---
title: "Agrupaci&#243;n de recursos en una aplicaci&#243;n OLE DB | Microsoft Docs"
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
  - "proveedores OLE DB, agrupación de recursos"
  - "servicios OLE DB [OLE DB], agrupación de recursos"
  - "OLE DB, agrupación de recursos"
  - "agrupación de recursos [OLE DB], servicios"
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agrupaci&#243;n de recursos en una aplicaci&#243;n OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para aprovechar la agrupación en la aplicación, debe asegurarse de que se invocan los servicios OLE DB obteniendo el origen de datos a través de **IDataInitialize** o **IDBPromptInitialize**.  Si utiliza `CoCreateInstance` directamente para invocar al proveedor a partir de su CLSID, no se invocará ningún servicio OLE DB.  
  
 Los servicios OLE DB mantienen grupos de orígenes de datos conectados mientras se mantenga una referencia a **IDataInitialize** o **IDBPromptInitialize**, o bien mientras se esté utilizando una conexión.  Los grupos también se mantienen automáticamente en un entorno de Servicios COM\+ 1.0 o de Internet Information Services \(IIS\).  Si la aplicación utiliza la agrupación fuera de un entorno de Servicios COM\+ 1.0 o IIS, debe conservar una referencia a **IDataInitialize** o **IDBPromptInitialize**, o bien mantener una conexión como mínimo.  Para asegurarse de que no se destruya el grupo cuando la aplicación libere la última conexión, mantenga la referencia o mantenga la conexión mientras dure la ejecución de la aplicación.  
  
 Los servicios OLE DB identifican el grupo desde el que se retirará la conexión cuando se llame a `Initialize`.  Después de retirar la conexión de un grupo, no se podrá mover a un grupo diferente.  Por tanto, debe evitar que la aplicación haga que cambie la información de inicialización, como llamar a `UnInitialize` o a `QueryInterface` para obtener una interfaz específica del proveedor antes de llamar a `Initialize`.  Además, no se agruparán las conexiones establecidas con un valor de pregunta distinto de **DBPROMPT\_NOPROMPT**.  Sin embargo, la cadena de inicialización recuperada desde una conexión establecida mediante pregunta al usuario puede utilizarse para establecer conexiones agrupadas adicionales al mismo origen de datos.  
  
 Algunos proveedores deben establecer una conexión independiente para cada sesión.  Estas conexiones adicionales deben alistarse por separado en la transacción distribuida \(si existe alguna\).  Los servicios OLE DB almacenan en caché y reutilizan una sola sesión por cada origen de datos, pero si la aplicación solicita varias sesiones a la vez de un solo origen de datos, el proveedor podría acabar creando más conexiones y alistando transacciones adicionales que no se agrupan.  En realidad es más eficaz crear un origen de datos independiente para cada sesión en un entorno agrupado que crear varias sesiones desde un único origen de datos.  
  
 Por último, puesto que ADO utiliza automáticamente servicios de OLE DB, puede usar ADO para establecer conexiones. Se realizarán automáticamente tanto la agrupación como el alistamiento.  
  
## Vea también  
 [Servicios y agrupación de recursos OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)