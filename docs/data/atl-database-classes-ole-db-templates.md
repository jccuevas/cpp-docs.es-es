---
title: "Clases de base de datos ATL (plantillas OLE DB) | Microsoft Docs"
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
  - "clases de base de datos [C++], ATL"
  - "clases de base de datos [C++], OLE DB"
  - "plantillas OLE DB [C++], clases de base de datos ATL"
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Clases de base de datos ATL (plantillas OLE DB)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft proporciona varias implementaciones de OLE DB, un conjunto de interfaces COM que proporcionan acceso universal a los datos en diferentes orígenes de datos y formatos.  
  
 Las plantillas OLE DB son plantillas de C\+\+ de la biblioteca ATL que hacen más fácil de utilizar la tecnología de bases de datos de alto rendimiento OLE DB, al proporcionar clases que implementan muchas de las interfaces OLE DB más utilizadas.  
  
 Esta biblioteca de plantillas se compone de dos partes:  
  
-   [Plantillas de consumidor OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) Se utilizan para implementar una aplicación de cliente \(consumidor\) OLE DB.  
  
-   [Plantillas de proveedor OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) Se utilizan para implementar una aplicación de servidor \(proveedor\) OLE DB.  
  
 Asimismo, los [atributos de consumidor OLE DB](../windows/ole-db-consumer-attributes.md) proporcionan una forma cómoda de crear consumidores OLE DB.  Los atributos OLE DB insertan código basado en las plantillas de consumidor OLE DB para crear consumidores OLE DB en funcionamiento.  
  
 Observe que la biblioteca MFC contiene una clase, [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), que muestra los registros de una base de datos en controles.  La vista es una vista de formulario directamente conectada a un objeto `CRowset`, y muestra los campos del objeto `CRowset` en los controles de la plantilla de cuadro de diálogo.  
  
 Para obtener más información, vea [Programación de OLE DB](../data/oledb/ole-db-programming.md) y [La guía del programador de OLE DB](http://go.microsoft.com/fwlink/?LinkId=121548).  
  
## Vea también  
 [Crear un consumidor OLE DB](../data/oledb/creating-an-ole-db-consumer.md)   
 [Crear un proveedor OLE DB](../data/oledb/creating-an-ole-db-provider.md)   
 [Referencia de plantillas de consumidor OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)   
 [Referencia de plantillas de proveedores OLE DB](../data/oledb/ole-db-provider-templates-reference.md)   
 [OLE DB Templates Samples](http://msdn.microsoft.com/es-es/08958863-0b5f-41ad-ae99-fca7440c553c)