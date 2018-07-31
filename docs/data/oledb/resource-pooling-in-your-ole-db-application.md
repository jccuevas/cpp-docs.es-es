---
title: Agrupación de recursos en una aplicación OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4798b4bac8cc6f94e5199502a926eb084cc7534a
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340246"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Agrupación de recursos en una aplicación OLE DB
Para aprovechar la agrupación en la aplicación, debe asegurarse de que se invocan servicios OLE DB obteniendo el origen de datos a través de `IDataInitialize` o `IDBPromptInitialize`. Si utiliza directamente `CoCreateInstance` para invocar el proveedor basándose en el CLSID del proveedor, se invocan los servicios OLE DB.  
  
 Los servicios de OLE DB mantienen grupos de orígenes de datos conectados tan largos como una referencia a `IDataInitialize` o `IDBPromptInitialize` se mantiene o siempre y cuando hay una conexión en uso. Los grupos también se mantienen automáticamente dentro de un entorno de servicios COM + 1.0 o Internet Information Services (IIS). Si la aplicación aprovecha la agrupación fuera de un entorno de servicios COM + 1.0 o IIS, debe mantener una referencia a `IDataInitialize` o `IDBPromptInitialize` o conserve al menos una conexión. Para asegurarse de que no se destruya el grupo cuando se libere la última conexión por la aplicación, mantener la referencia o mantenga la conexión durante la vigencia de la aplicación.  
  
 Servicios OLE DB identifican el grupo desde el que se dibuja la conexión al tiempo que `Initialize` se llama. Después de dibuja la conexión de un grupo, no se pueden mover a otro grupo. Por lo tanto, evitar hacer cosas en la aplicación que cambie la información de inicialización, como la llamada a `UnInitialize` o llamar a `QueryInterface` para una interfaz específica del proveedor antes de llamar a `Initialize`. Además, no se agrupan las conexiones establecidas con un valor distinto de DBPROMPT_NOPROMPT del mensaje. Sin embargo, la cadena de inicialización recuperada de una conexión establecida a través de preguntar puede utilizarse para establecer conexiones agrupadas adicionales al mismo origen de datos.  
  
 Algunos proveedores deben establecer una conexión independiente para cada sesión. Estas conexiones adicionales deben estar inscrito por separado en la transacción distribuida, si existe alguno. Servicios OLE DB se almacena en caché y vuelve a usar una única sesión de cada origen de datos, pero si la aplicación solicita más de una sesión a la vez desde un único origen de datos, el proveedor podría acabar realizar conexiones adicionales y realizar inscripciones de transacción adicionales que son no agrupados. Es realmente más eficaz para crear un origen de datos independiente para cada sesión en un entorno agrupado que crear varias sesiones desde un único origen de datos.  
  
 Por último, dado que ADO automáticamente hace uso de OLE DB services, puede utilizar ADO para establecer conexiones y la agrupación y la inscripción se realiza automáticamente.  
  
## <a name="see-also"></a>Vea también  
 [Servicios y agrupación de recursos OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)