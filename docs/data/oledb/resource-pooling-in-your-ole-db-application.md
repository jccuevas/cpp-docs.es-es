---
title: Agrupación de recursos en una aplicación OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: 3604f6eaaf0f34a0ff7e54826923c2aa92eef4a2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209800"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Agrupación de recursos en una aplicación OLE DB

Para aprovechar la agrupación en la aplicación, debe asegurarse de que OLE DB servicios se invocan obteniendo el origen de datos a través de `IDataInitialize` o `IDBPromptInitialize`. Si usa directamente `CoCreateInstance` para invocar el proveedor basándose en el CLSID del proveedor, no se invoca ningún servicio de OLE DB.

Los servicios de OLE DB mantienen grupos de orígenes de datos conectados, siempre que se mantenga una referencia a `IDataInitialize` o `IDBPromptInitialize`, o siempre que haya una conexión en uso. Los grupos también se mantienen automáticamente dentro de un entorno de servicios o Internet Information Services de COM+ 1,0 (IIS). Si la aplicación saca partido de la agrupación externa a un entorno de IIS o servicios COM+ 1,0, debe mantener una referencia a `IDataInitialize` o `IDBPromptInitialize` o mantener en al menos una conexión. Para asegurarse de que el grupo no se destruye cuando la aplicación libera la última conexión, conserve la referencia o mantenga en la conexión la duración de la aplicación.

Los servicios de OLE DB identifican el grupo desde el que se dibuja la conexión en el momento en que se llama a `Initialize`. Una vez que se ha extraído la conexión de un grupo, no se puede pasar a un grupo diferente. Por lo tanto, Evite hacer cosas en la aplicación que cambien la información de inicialización, como llamar a `UnInitialize` o llamar a `QueryInterface` para una interfaz específica del proveedor antes de llamar a `Initialize`. Además, las conexiones establecidas con un valor de aviso distinto de DBPROMPT_NOPROMPT no se agrupan. Sin embargo, la cadena de inicialización recuperada de una conexión establecida a través de la solicitud se puede usar para establecer conexiones agrupadas adicionales en el mismo origen de datos.

Algunos proveedores deben establecer una conexión independiente para cada sesión. Estas conexiones adicionales se deben dar de alta por separado en la transacción distribuida, si existe una. OLE DB Services almacena en caché y reutiliza una sola sesión por origen de datos, pero si la aplicación solicita más de una sesión a la vez desde un único origen de datos, el proveedor puede acabar realizando conexiones adicionales y realizando inlistas de transacciones adicionales que no están agrupadas. Es más eficaz crear un origen de datos independiente para cada sesión en un entorno agrupado que crear varias sesiones desde un único origen de datos.

Por último, dado que ADO usa automáticamente OLE DB Services, puede usar ADO para establecer conexiones y la agrupación y la inscripción se producen automáticamente.

## <a name="see-also"></a>Consulte también

[Servicios y agrupación de recursos OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)
