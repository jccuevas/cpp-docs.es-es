---
title: Agrupación de recursos en una aplicación OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: 786c2b31bb93b0691d80885c86377e2afba8c1dc
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029309"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Agrupación de recursos en una aplicación OLE DB

Para aprovechar la agrupación en la aplicación, debe asegurarse de que se invocan servicios OLE DB obteniendo el origen de datos a través de `IDataInitialize` o `IDBPromptInitialize`. Si utiliza directamente `CoCreateInstance` para invocar el proveedor basándose en el CLSID del proveedor, se invocan los servicios OLE DB.

Los servicios de OLE DB mantienen grupos de orígenes de datos conectados tan largos como una referencia a `IDataInitialize` o `IDBPromptInitialize` se mantiene o siempre y cuando hay una conexión en uso. Los grupos también se mantienen automáticamente dentro de un entorno de servicios COM + 1.0 o Internet Information Services (IIS). Si la aplicación aprovecha las ventajas de la agrupación de externo en un entorno de servicios COM + 1.0 o IIS, debe mantener una referencia a `IDataInitialize` o `IDBPromptInitialize` o conserve al menos una conexión. Para asegurarse de que no se destruya el grupo cuando se libere la última conexión por la aplicación, mantener la referencia o mantenga la conexión durante la vigencia de la aplicación.

Servicios OLE DB identifican el grupo desde el que se dibuja la conexión al tiempo que `Initialize` se llama. Después de dibuja la conexión de un grupo, no se pueden mover a otro grupo. Por lo tanto, evitar hacer cosas en la aplicación que cambie la información de inicialización, como la llamada a `UnInitialize` o llamar a `QueryInterface` para una interfaz específica del proveedor antes de llamar a `Initialize`. Además, no se agrupan conexiones establecidas con un valor distinto de DBPROMPT_NOPROMPT del mensaje. Sin embargo, la cadena de inicialización recuperada de una conexión establecida a través de preguntar puede utilizarse para establecer conexiones agrupadas adicionales al mismo origen de datos.

Algunos proveedores deben establecer una conexión independiente para cada sesión. Estas conexiones adicionales deben estar inscrito por separado en la transacción distribuida, si existe alguno. OLE DB services las memorias caché y vuelve a usar una única sesión de cada origen de datos, pero si la aplicación solicita más de una sesión a la vez desde un único origen de datos, el proveedor podría acabar realizar conexiones adicionales y realizar inscripciones de transacción adicionales que no se agrupan. Resulta más eficaz para crear un origen de datos independiente para cada sesión en un entorno agrupado que crear varias sesiones desde un único origen de datos.

Por último, dado que ADO automáticamente hace uso de OLE DB services, puede utilizar ADO para establecer conexiones y la agrupación y la inscripción se realiza automáticamente.

## <a name="see-also"></a>Vea también

[Servicios y agrupación de recursos OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)