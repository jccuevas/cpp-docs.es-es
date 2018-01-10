---
title: "Problemas de diseño de la arquitectura de OLE DB | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b894ec1cbd227663d46e98e523ffe8c1c5d84475
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="ole-db-architectural-design-issues"></a>Cuestiones de diseño de arquitectura OLE DB
Debe considerar lo siguiente antes de iniciar una aplicación OLE DB:  
  
 **¿Qué implementación de programación va a utilizar para escribir una aplicación OLE DB?**  
 Microsoft ofrece varias bibliotecas para lograr esto: una biblioteca de plantillas OLE DB, atributos OLE DB y las interfaces OLE DB sin formato en el SDK de OLE DB. Además, hay asistentes que le ayudan a escribir su programa. Estas implementaciones se describen en [plantillas OLE DB, atributos y otras implementaciones](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).  
  
 **¿Es necesario escribir su propio proveedor?**  
 Mayoría de los desarrolladores no es necesario escribir su propio proveedor. Microsoft proporciona varios proveedores. Siempre que se crea una conexión de datos (por ejemplo, al agregar un consumidor al proyecto mediante el Asistente para consumidores OLE DB ATL), el **propiedades de vínculo de datos** cuadro de diálogo muestra todos los proveedores disponibles registrados en el sistema. Si uno de estos proveedores es adecuado para su propia aplicación de acceso de datos y el almacén de datos, lo más fácil es utilizar uno de ellos. Sin embargo, si el almacén de datos no encaja en ninguna de estas categorías, deberás crear su propio proveedor. Para obtener información sobre la creación de proveedores, consulte [plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
 **¿Qué nivel de compatibilidad es necesario para el consumidor?**  
 Algunos consumidores pueden ser muy básicas; mientras que otros pueden ser muy complejos. La funcionalidad de objetos OLE DB especificada por propiedades. Cuando usa el Asistente para consumidores OLE DB ATL para crear un consumidor o el Asistente para proveedores de base de datos para crear un proveedor, Establece las propiedades del objeto adecuado para usted para ofrecerle un conjunto estándar de funcionalidades. Sin embargo, si las clases de consumidor o proveedor generadas por el asistente no admiten todo lo que necesita llevar a cabo, debe hacer referencia a las interfaces de dichas clases en el [biblioteca de plantillas OLE DB](../../data/oledb/ole-db-templates.md). Estas interfaces envuelven las interfaces OLE DB sin formato, proporcionando una implementación adicional para facilitar su uso por usted.  
  
 Por ejemplo, si desea actualizar los datos de un conjunto de filas, pero que se haya olvidado de especificarlo al crear el consumidor con el asistente, puede especificar la funcionalidad posteriori estableciendo la **DBPROP_IRowsetChange** y  **DBPROP_UPDATABILITY** propiedades en el objeto de comando. A continuación, cuando se crea el conjunto de filas, tiene la `IRowsetChange` interfaz.  
  
 **¿Tiene código antiguo con otra tecnología de acceso a datos (ADO, ODBC o DAO)?**  
 Dadas las posibles combinaciones de tecnologías (por ejemplo, usar componentes ADO con componentes OLE DB y migrar código ODBC a OLE DB), que abarca todas las situaciones queda fuera del ámbito de la documentación de Visual C++. Sin embargo, muchos artículos que tratan diversos escenarios están disponibles en los siguientes sitios Web de Microsoft:  
  
-   [Ayuda y Soporte Técnico de Microsoft](http://go.microsoft.com/fwlink/p/?linkid=148218)  
  
-   [Información general de artículos técnicos de Microsoft Data Access](http://go.microsoft.com/fwlink/p/?linkid=148217)  
  
-   [Centro de soluciones de Visual Studio](http://go.microsoft.com/fwlink/p/?linkid=148215)  
  
-   [Buscar en Microsoft.com](http://search.microsoft.com/)  
  
 Al realizar una búsqueda, escriba una combinación de palabras clave que mejor se adapte a su escenario; Por ejemplo: si se utiliza objetos ADO con un proveedor OLE DB, intente una búsqueda booleana con **ADO AND "OLE DB"**. Si desea migrar código DAO antiguo a ODBC, seleccione "todas las palabras" y especifique cadenas como **DAO migrar**.  
  
## <a name="see-also"></a>Vea también  
 [Programación de OLE DB](../../data/oledb/ole-db-programming.md)   
 [Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)