---
title: Clases de base de datos ATL (plantillas OLE DB) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fabced79232d17807d252da9dac5b066ddf69f25
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="atl-database-classes-ole-db-templates"></a>Clases de base de datos ATL (plantillas OLE DB)
Microsoft proporciona varias implementaciones de OLE DB, un conjunto de interfaces COM que proporcionan acceso uniforme a los datos de diversos orígenes de información y formatos.  OLE DB esté oficialmente en desuso; Esta documentación es para los desarrolladores que están realizando el mantenimiento del código heredado. Aplicaciones nuevas deben usar ODBC para conectarse a orígenes de datos SQL.
  
 Las plantillas OLE DB son plantillas de C++ en ATL que facilitan la tecnología de base de datos de OLE DB utilizar al proporcionar clases que implementan muchas de las interfaces OLE DB más utilizadas.  
  
 Esta biblioteca de plantillas consta de dos partes:  
  
-   [Plantillas de consumidor OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) usado para implementar una aplicación de cliente (consumidor) OLE DB.  
  
-   [Plantillas del proveedor OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) usado para implementar una aplicación de servidor (proveedor) OLE DB.  
  
 Además, el [atributos de consumidor OLE DB](../windows/ole-db-consumer-attributes.md) proporcionan una manera cómoda de crear consumidores OLE DB. Los atributos OLE DB insertan código basado en las plantillas de consumidor OLE DB para crear consumidores OLE DB en funcionamiento.  
  
 Observe que la biblioteca MFC contiene una clase, [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), que muestra registros de base de datos en controles. La vista es una vista de formulario directamente conectada a un `CRowset` de objetos y muestra los campos de la `CRowset` objeto en los controles de la plantilla de cuadro de diálogo.  
  
 Para obtener más información, consulte [programación de OLE DB](../data/oledb/ole-db-programming.md) y [Guía del programador de OLE DB](http://go.microsoft.com/fwlink/p/?linkid=121548).  
  
## <a name="see-also"></a>Vea también  
 [Crear un consumidor OLE DB](../data/oledb/creating-an-ole-db-consumer.md)   
 [Crear un proveedor OLE DB](../data/oledb/creating-an-ole-db-provider.md)   
 [Referencia de plantillas de consumidor OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)   
 [Referencia de plantillas del proveedor OLE DB](../data/oledb/ole-db-provider-templates-reference.md)   
 [Ejemplos de plantillas OLE DB](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)