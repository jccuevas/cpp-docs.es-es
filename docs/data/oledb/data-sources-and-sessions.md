---
title: Orígenes de datos y sesiones
ms.date: 11/19/2018
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
ms.openlocfilehash: 0514f6a9285936c85608f08774c1d377fd72d6ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211060"
---
# <a name="data-sources-and-sessions"></a>Orígenes de datos y sesiones

En la ilustración siguiente se muestran las clases que admiten la conexión y el acceso a un origen de datos. Cada clase se basa en una implementación de componente de OLE DB estándar.

![Clases de origen de datos y de sesión](../../data/oledb/media/vcdatasourcesessionclasses.gif "Clases de origen de datos y sesión") <br/>
Clases de origen de datos y sesión

Las clases son:

- [CDataSource](../../data/oledb/cdatasource-class.md) Esta clase crea instancias del objeto de origen de datos, que crea y administra una conexión a un origen de datos a través de un proveedor de OLE DB. El origen de datos toma información como la dirección del origen de datos y la información de autenticación en forma de cadena de conexión.

   También merece la pena tener en cuenta que la clase auxiliar [CEnumerator](../../data/oledb/cenumerator-class.md) se suele usar antes de establecer una conexión para obtener una lista de proveedores disponibles registrados en un sistema. Esto le permite seleccionar un proveedor como origen de datos. Por ejemplo, el cuadro de diálogo **propiedades de vínculo de datos** utiliza esta clase para rellenar la lista de proveedores en la pestaña **proveedores** . Equivale a la función `SQLBrowseConnect` o `SQLDriverConnect`.

- [CSession](../../data/oledb/csession-class.md) Esta clase crea instancias del objeto de sesión, que representa una sesión de acceso única para el origen de datos. Sin embargo, puede crear varias sesiones en un origen de datos. Para cada sesión, puede crear conjuntos de filas, comandos y otros objetos para tener acceso a los datos del origen de datos. La sesión controla las transacciones.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)
