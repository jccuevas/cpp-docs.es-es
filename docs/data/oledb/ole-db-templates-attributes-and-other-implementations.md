---
title: "Plantillas, atributos y otras implementaciones de OLE DB | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plantillas OLE DB"
  - "plantillas OLE DB, acerca de las plantillas OLE DB"
  - "OLE DB, implementaciones"
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Plantillas, atributos y otras implementaciones de OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Plantillas OLE DB de ATL  
 Las plantillas OLE DB, que forman parte de ATL \(Active Template Library\), hacen más fácil de utilizar la tecnología de bases de datos de alto rendimiento OLE DB, al proporcionar clases que implementan muchas de las interfaces OLE DB más utilizadas.  Junto con esta biblioteca de plantillas se proporcionan asistentes para la creación de aplicaciones sencillas OLE DB.  
  
 Esta biblioteca de plantillas se compone de dos partes:  
  
-   **Plantillas de consumidor OLE DB** Se utilizan para implementar una aplicación de cliente \(consumidor\) OLE DB.  
  
-   **Plantillas de proveedor OLE DB** Se utilizan para implementar una aplicación de servidor \(proveedor\) OLE DB.  
  
 Para utilizar las plantillas OLE DB, se debe estar familiarizado con las plantillas de C\+\+, COM y las interfaces OLE DB.  Si no está familiarizado con OLE DB, vea [Referencia del programador de OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx).  
  
 Para obtener más información, pruebe lo siguiente:  
  
-   Lea los temas [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) o [Plantillas de proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
-   Cree un [consumidor OLE DB](../../data/oledb/creating-an-ole-db-consumer.md) o un [proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md).  
  
-   Vea la lista de [clases de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) o de [clases de proveedor OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).  
  
-   Vea la lista de [ejemplos de plantillas OLE DB](http://msdn.microsoft.com/es-es/08958863-0b5f-41ad-ae99-fca7440c553c).  
  
-   Vea [Referencia del programador de OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx) \(en [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)]\).  
  
## Atributos OLE DB  
 Los [atributos de consumidor OLE DB](../../windows/ole-db-consumer-attributes.md) proporcionan una forma cómoda de crear consumidores OLE DB.  Los atributos OLE DB insertan código basado en las [plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) para crear consumidores y proveedores OLE DB en funcionamiento.  Si necesita especificar funcionalidad no compatible con los atributos, puede utilizar las plantillas OLE DB junto con los atributos utilizados en el código.  
  
## Clases OLE DB de MFC  
 La biblioteca MFC contiene una clase, [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), que muestra los registros de una base de datos en controles.  La vista es una vista de formulario directamente conectada a un objeto `CRowset` y muestra los campos del objeto `CRowset` en los controles de la plantilla de cuadro de diálogo.  También proporciona una implementación predeterminada para desplazarse al primer, siguiente, anterior o último registro y una interfaz para actualizar el registro mostrado actualmente en la vista.  Para obtener más información, vea `COleDBRecordView`.  
  
## Interfaces del SDK de OLE DB  
 En los casos en los que las plantillas OLE DB no admiten la funcionalidad de OLE DB, es necesario usar las propias interfaces de OLE DB.  Para obtener más información, vea la [Referencia del programador de OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx) en [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)].  
  
## Vea también  
 [Programación de OLE DB](../../data/oledb/ole-db-programming.md)   
 [Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)