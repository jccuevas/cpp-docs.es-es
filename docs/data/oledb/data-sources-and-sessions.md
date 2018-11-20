---
title: Orígenes de datos y sesiones
ms.date: 11/19/2018
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
ms.openlocfilehash: c43061ccb462fe472821c76251430b5e3b0f0809
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175306"
---
# <a name="data-sources-and-sessions"></a>Orígenes de datos y sesiones

La siguiente ilustración muestra las clases que permiten conectar y obtener acceso a un origen de datos. Cada clase se basa en una implementación de componentes OLE DB estándar.

![Las clases de sesión y el origen de datos](../../data/oledb/media/vcdatasourcesessionclasses.gif "clases de sesión y el origen de datos") <br/>
Clases de origen de datos y sesión

Las clases son:

- [CDataSource](../../data/oledb/cdatasource-class.md) esta clase crea una instancia del objeto de origen de datos, que crea y administra una conexión a un origen de datos a través de un proveedor OLE DB. El origen de datos toma información como la información de autenticación y la dirección de origen de datos en forma de una cadena de conexión.

   También merece la pena mencionar que la clase auxiliar [CEnumerator](../../data/oledb/cenumerator-class.md) a menudo se usa antes de establecer una conexión para obtener una lista de proveedores disponibles y registrados en un sistema. Esto le permite seleccionar un proveedor como un origen de datos. Por ejemplo, el **propiedades de vínculo de datos** cuadro de diálogo usa esta clase para rellenar la lista de proveedores de la **proveedores** ficha. Equivale a la `SQLBrowseConnect` o `SQLDriverConnect` función.

- [CSession](../../data/oledb/csession-class.md) esta clase crea instancias del objeto de sesión, que representa una sesión única de acceso al origen de datos. Sin embargo, puede crear varias sesiones en un origen de datos. Para cada sesión, puede crear conjuntos de filas, comandos y otros objetos para tener acceso a datos desde el origen de datos. La sesión controla las transacciones.

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)