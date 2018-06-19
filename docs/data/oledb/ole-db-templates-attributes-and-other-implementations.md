---
title: Plantillas OLE DB, atributos y otras implementaciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ef9baf43ded1533eb7f4962db7344f9dc1def0ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111177"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>Plantillas, atributos y otras implementaciones de OLE DB
## <a name="atl-ole-db-templates"></a>Plantillas OLE DB de ATL  
 Las plantillas OLE DB, que forman parte de ATL (Active Template Library), que la tecnología de base de datos de OLE DB de alto rendimiento más fácil usar al proporcionar clases que implementan muchas de las interfaces OLE DB más utilizadas. Junto con esta plantilla Biblioteca incluye compatibilidad de Asistente para crear aplicaciones sencillas OLE DB.  
  
 Esta biblioteca de plantillas consta de dos partes:  
  
-   **Plantillas de consumidor OLE DB** usado para implementar una aplicación de cliente (consumidor) OLE DB.  
  
-   **Plantillas del proveedor OLE DB** usado para implementar una aplicación de servidor (proveedor) OLE DB.  
  
 Para usar las plantillas OLE DB, es necesario estar familiarizado con las plantillas de C++, COM y las interfaces OLE DB. Si no está familiarizado con OLE DB, vea [referencia del programador de OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx).  
  
 Para obtener más información, hacer lo siguiente:  
  
-   Lea los temas sobre la [plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) o [plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
-   Crear un [consumidor OLE DB](../../data/oledb/creating-an-ole-db-consumer.md) o [proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md).  
  
-   Ver la lista de [clases de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) o [clases de proveedor OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).  
  
-   Ver la lista de [ejemplos de plantillas OLE DB](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c).  
  
-   Vea [referencia del programador OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx) (en el SDK de Windows).  
  
## <a name="ole-db-attributes"></a>Atributos de OLE DB  
 El [atributos de consumidor OLE DB](../../windows/ole-db-consumer-attributes.md) proporcionan una manera cómoda de crear consumidores OLE DB. Los atributos OLE DB insertan código basado en la [plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) para crear consumidores OLE DB en funcionamiento y proveedores. Si tiene que especificar funciones no admitidas por los atributos, puede utilizar las plantillas OLE DB junto con atributos en el código.  
  
## <a name="mfc-ole-db-classes"></a>Clases MFC OLE DB  
 La biblioteca MFC contiene una clase, [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), que muestra registros de base de datos en controles. La vista es una vista de formulario directamente conectada a un `CRowset` objeto y muestra los campos de la `CRowset` objeto en los controles de la plantilla de cuadro de diálogo. También proporciona una implementación predeterminada para desplazarse a la primera, siguiente, anterior o el último registro y una interfaz para actualizar el registro actualmente en la vista. Para obtener más información, consulta `COleDBRecordView`.  
  
## <a name="ole-db-sdk-interfaces"></a>Interfaces SDK de OLE DB  
 En los casos donde las plantillas OLE DB no admiten la funcionalidad de OLE DB, debe usar sus propias interfaces de OLE DB. Para obtener más información, consulte [referencia del programador de OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Programación de OLE DB](../../data/oledb/ole-db-programming.md)   
 [Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)