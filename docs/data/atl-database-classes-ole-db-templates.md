---
title: Clases de base de datos ATL (plantillas OLE DB)
ms.date: 05/02/2019
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: dc016a5e1e1d9652f6a69f73b5760f42dec5e889
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222560"
---
# <a name="atl-database-classes-ole-db-templates"></a>Clases de base de datos ATL (plantillas OLE DB)

Microsoft proporciona varias implementaciones de OLE DB, un conjunto de interfaces COM que proporcionan acceso uniforme a datos de diversos orígenes de información y formatos.

Las plantillas OLE DB son plantillas de C++ en ATL que facilitan la tecnología de base de datos de OLE DB usar al proporcionar clases que implementan muchas de las interfaces OLE DB más utilizadas.

Esta biblioteca de plantillas contiene dos partes:

- [Plantillas de consumidor OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) usado para implementar una aplicación de cliente (consumidor) de OLE DB.

- [Plantillas de proveedores OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) usado para implementar una aplicación de servidor (proveedor) de OLE DB.

Además, el [atributos de consumidor OLE DB](../windows/ole-db-consumer-attributes.md) proporcionan una manera cómoda para crear consumidores OLE DB. Los atributos OLE DB insertan código basado en las plantillas de consumidor OLE DB para crear consumidores OLE DB de trabajo.

Observe que la biblioteca MFC contiene una clase, [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), que muestra los registros de base de datos en controles. La vista es una vista de formulario conectada directamente a un `CRowset` de objetos y muestra los campos de la `CRowset` objeto en los controles de la plantilla de cuadro de diálogo.

Para obtener más información, consulte [programación de OLE DB](../data/oledb/ole-db-programming.md) y [Guía del programador de OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

## <a name="see-also"></a>Vea también

[Crear un consumidor OLE DB](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[Crear un proveedor OLE DB](../data/oledb/creating-an-ole-db-provider.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Referencia de plantillas de proveedores OLE DB](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Ejemplos de plantillas OLE DB](https://github.com/Microsoft/VCSamples)
