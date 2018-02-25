---
title: "Agrupación de recursos en una aplicación OLE DB | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 84b8814974850238ccf0be7411821d6e2cce8880
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Agrupación de recursos en una aplicación OLE DB
Para aprovechar la agrupación en la aplicación, debe asegurarse de que se invocan los servicios OLE DB obteniendo el origen de datos a través de **IDataInitialize** o **IDBPromptInitialize**. Si utiliza directamente `CoCreateInstance` para invocar el proveedor basándose en el CLSID del proveedor, se invocan los servicios OLE DB.  
  
 Los servicios de OLE DB mantienen grupos de orígenes de datos conectados siempre que una referencia a **IDataInitialize** o **IDBPromptInitialize** es mantenido o siempre que haya una conexión en uso. Los grupos también se mantienen automáticamente dentro de un entorno de servicios COM + 1.0 o Internet Information Services (IIS). Si la aplicación aprovecha las ventajas de agrupación fuera de un entorno de servicios COM + 1.0 o IIS, debe mantener una referencia a **IDataInitialize** o **IDBPromptInitialize** o retener uno como mínimo conexión. Para asegurarse de que el grupo no se destruya cuando se libere la última conexión por la aplicación, mantener la referencia o mantenga la conexión durante la vigencia de la aplicación.  
  
 Servicios OLE DB identifican el grupo desde el que se dibuja la conexión en el momento en que `Initialize` se llama. Una vez dibujada la conexión de un grupo, no se puede mover a otro grupo diferente. Por lo tanto, evitar hacer las cosas en la aplicación que cambiar la información de inicialización, como la llamada a `UnInitialize` o llamando a `QueryInterface` para una interfaz específica del proveedor antes de llamar a `Initialize`. Además, las conexiones establecidas con un valor de mensaje distinto de **DBPROMPT_NOPROMPT** no están agrupadas. Sin embargo, la cadena de inicialización recuperada desde una conexión establecida mediante pregunta al usuario puede utilizarse para establecer conexiones agrupadas adicionales al mismo origen de datos.  
  
 Algunos proveedores deben establecer una conexión independiente para cada sesión. Estas conexiones adicionales deben estar inscrito por separado en la transacción distribuida, si existe alguno. Servicios OLE DB se almacena en caché y se vuelve a utilizar una sola sesión por cada origen de datos, pero si la aplicación solicita más de una sesión a la vez desde un único origen de datos, el proveedor podría acabar creando conexiones adicionales y realizar inscripciones de transacción adicionales que son no agrupados. Es realmente más eficaz para crear un origen de datos independiente para cada sesión en un entorno agrupado que crear varias sesiones desde un único origen de datos.  
  
 Por último, porque ADO automáticamente hace que el uso de OLE DB services, puede utilizar ADO para establecer conexiones y la agrupación y la inscripción se producen automáticamente.  
  
## <a name="see-also"></a>Vea también  
 [Servicios y agrupación de recursos OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)