---
title: "Cuestiones de dise&#241;o de arquitectura OLE DB | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB, consideraciones sobre el diseño de aplicaciones"
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cuestiones de dise&#241;o de arquitectura OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se deben considerar las siguientes cuestiones antes de comenzar a desarrollar una aplicación OLE DB:  
  
 **¿Qué implementación de programación se va a utilizar para crear la aplicación OLE DB?**  
 Microsoft ofrece varias bibliotecas para este proceso: una biblioteca de plantillas OLE DB, atributos OLE DB y las interfaces OLE DB sin formato del SDK de OLE DB.  Asimismo, hay asistentes que le ayudarán a escribir su programa.  Estas implementaciones se describen en [Plantillas, atributos y otras implementaciones de OLE DB](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).  
  
 **¿Necesita crear su propio proveedor?**  
 La mayoría de los desarrolladores no necesitan escribir su propio proveedor.  Microsoft proporciona varios proveedores.  Siempre que cree una conexión de datos \(por ejemplo, al agregar un consumidor al proyecto con el Asistente para consumidores OLE DB ATL\), el cuadro de diálogo **Propiedades de vínculo de datos** mostrará todos los proveedores disponibles y registrados en el sistema.  Si uno de estos proveedores es apropiado para su almacén de datos y su aplicación de acceso a datos, lo más sencillo es utilizar uno de ellos.  Sin embargo, si el almacén de datos no encaja en ninguna de esas categorías, debe crear su propio proveedor.  Para obtener más información sobre la creación de proveedores, vea [Plantillas de proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
 **¿Qué nivel de compatibilidad necesita para su consumidor?**  
 Algunos consumidores pueden ser muy sencillos y otros muy complejos.  La funcionalidad de los objetos OLE DB se especifica a través de propiedades.  Al usar el Asistente para consumidores OLE DB ATL para crear un consumidor o el Asistente para proveedores OLE DB ATL para crear un proveedor, establece las propiedades correspondientes de los objetos para darle un conjunto estándar de funcionalidades.  Sin embargo, si las clases de consumidor o proveedor generadas por el asistente no admiten todo lo necesario para su aplicación, consulte las interfaces de dichas clases en la [Biblioteca de plantillas OLE DB](../../data/oledb/ole-db-templates.md).  Estas interfaces envuelven las interfaces sin formato de OLE DB, proporcionando una implementación adicional para que su uso sea más fácil.  
  
 Por ejemplo, si desea actualizar los datos de un conjunto de filas, pero se olvidó de especificarlo al crear el consumidor con el asistente, puede especificar esta funcionalidad con posterioridad estableciendo las propiedades **DBPROP\_IRowsetChange** y **DBPROP\_UPDATABILITY** en el objeto de comando.  Después, una vez creado el conjunto de filas, tiene la interfaz `IRowsetChange`.  
  
 **Do you have older code using another data access technology \(ADO, ODBC, or DAO\)?**  
 Dadas las posibles combinaciones de tecnologías \(por ejemplo, usar componentes ADO con componentes OLE DB, o migrar código ODBC a OLE DB\), abarcar todos los casos queda fuera del ámbito de la documentación de Visual C\+\+.  Sin embargo, hay disponibles numerosos artículos que cubren diferentes situaciones en los siguientes sitios Web de Microsoft:  
  
-   [Ayuda y soporte](http://go.microsoft.com/fwlink/?LinkId=148218)  
  
-   [Información general técnica de los casos de acceso a datos de Microsoft](http://go.microsoft.com/fwlink/?LinkId=148217)  
  
-   [Centro de soluciones de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=148215)  
  
-   [Buscar Microsoft.com](http://search.microsoft.com/)  
  
 Al realizar una búsqueda, introduzca la combinación de palabras clave que mejor se ajuste a su escenario; por ejemplo: si utiliza objetos ADO con un proveedor OLE DB, intente una búsqueda booleana con **ADO AND "OLE DB"**.  Si desea migrar un anterior código DAO a ODBC, seleccione “todas las palabras” y especifique cadenas como **migrating DAO**.  
  
## Vea también  
 [Programación de OLE DB](../../data/oledb/ole-db-programming.md)   
 [Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)