---
title: Clases de base de datos ATL (plantillas OLE DB)
ms.date: 05/02/2019
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: 76e9f49d4b394d0c807ca1f3d103ff325ded8a09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213504"
---
# <a name="atl-database-classes-ole-db-templates"></a>Clases de base de datos ATL (plantillas OLE DB)

Microsoft proporciona varias implementaciones de OLE DB, un conjunto de interfaces COM que proporcionan acceso uniforme a los datos en diversos formatos y orígenes de información.

Las plantillas de OLE DB C++ son plantillas de ATL que facilitan el uso de la tecnología de base de datos de OLE DB al proporcionar clases que implementan muchas de las interfaces OLE DB de uso frecuente.

Esta biblioteca de plantillas contiene dos partes:

- [OLE DB plantillas de consumidor](../data/oledb/ole-db-consumer-templates-cpp.md) Se utiliza para implementar una aplicación de cliente de OLE DB (consumidor).

- [Plantillas de proveedor de OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) Se utiliza para implementar una aplicación de servidor de OLE DB (proveedor).

Además, los [atributos de consumidor OLE DB](../windows/ole-db-consumer-attributes.md) proporcionan una forma cómoda de crear OLE DB consumidores. Los atributos de OLE DB insertan código basado en las plantillas de consumidor OLE DB para crear OLE DB de trabajo de los consumidores.

Tenga en cuenta que la biblioteca MFC contiene una clase, [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), que muestra los registros de base de datos en los controles. La vista es una vista de formulario conectada directamente a un objeto `CRowset` y muestra los campos del objeto `CRowset` en los controles de la plantilla de cuadro de diálogo.

Para obtener más información, vea [OLE DB Programming](../data/oledb/ole-db-programming.md) and [OLE DB programmer's Guide](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

## <a name="see-also"></a>Consulte también

[Crear un consumidor OLE DB](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[Crear un proveedor OLE DB](../data/oledb/creating-an-ole-db-provider.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Referencia de plantillas de proveedores OLE DB](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Ejemplos de plantillas OLE DB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)
