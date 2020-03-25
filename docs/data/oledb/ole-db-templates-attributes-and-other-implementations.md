---
title: Plantillas, atributos y otras implementaciones de OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 722bfdf02dc89e061351fd2a87b5d019db10da6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209890"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>Plantillas, atributos y otras implementaciones de OLE DB

## <a name="atl-ole-db-templates"></a>Plantillas de OLE DB ATL

Las plantillas de OLE DB, que forman parte de ATL (Active Template Library), facilitan el uso de la tecnología de base de datos de OLE DB de alto rendimiento al proporcionar clases que implementan muchas de las interfaces de OLE DB que se usan habitualmente. Junto con esta biblioteca de plantillas, incluye compatibilidad con el Asistente para crear OLE DB aplicaciones de inicio.

Esta biblioteca de plantillas contiene dos partes:

- **OLE DB plantillas de consumidor** Se utiliza para implementar una aplicación de cliente de OLE DB (consumidor).

- **Plantillas de proveedor de OLE DB** Se utiliza para implementar una aplicación de servidor de OLE DB (proveedor).

Para usar las plantillas OLE DB, es necesario estar familiarizado con las plantillas de C++, COM y las interfaces OLE DB. Si no está familiarizado con OLE DB, consulte [la referencia del programador de OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

Para obtener más información, puede:

- Lea los temas sobre las plantillas de [consumidor de OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) o [las plantillas de proveedor de OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

- Cree un [OLE DB consumidor](../../data/oledb/creating-an-ole-db-consumer.md) o [OLE DB proveedor](../../data/oledb/creating-an-ole-db-provider.md).

- Vea la lista de clases de [consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) o [clases de proveedor de OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).

- Consulte la lista de [ejemplos de plantillas de OLE DB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB).

- Vea la [Referencia del programador de OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) (en el Windows SDK).

## <a name="ole-db-attributes"></a>Atributos de OLE DB

Los [atributos del consumidor OLE DB](../../windows/ole-db-consumer-attributes.md) proporcionan una forma cómoda de crear OLE DB consumidores. Los atributos de OLE DB insertan código basado en las [plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) para crear OLE DB consumidores y proveedores de trabajo. Si necesita especificar funcionalidad no admitida por los atributos, puede usar las plantillas de OLE DB junto con los atributos del código.

## <a name="mfc-ole-db-classes"></a>Clases de OLE DB MFC

La biblioteca MFC tiene una clase, [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), que muestra los registros de base de datos en los controles. La vista es una vista de formulario conectada directamente a un objeto `CRowset` y muestra los campos del objeto `CRowset` en los controles de la plantilla de cuadro de diálogo. También proporciona una implementación predeterminada para pasar al primer, siguiente, anterior o último registro y una interfaz para actualizar el registro que se encuentra actualmente en la vista. Para más información, consulte `COleDBRecordView`.

## <a name="ole-db-sdk-interfaces"></a>Interfaces del SDK de OLE DB

En los casos en los que las plantillas de OLE DB no admiten la funcionalidad de OLE DB, debe usar las interfaces de OLE DB. Para obtener más información, vea [Referencia del programador de OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Programación de OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)
