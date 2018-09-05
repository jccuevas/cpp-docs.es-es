---
title: Cuestiones de diseño de arquitectura OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b0a5c568a774d0aed05d702454664e653989401
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676841"
---
# <a name="ole-db-architectural-design-issues"></a>Cuestiones de diseño de arquitectura OLE DB
Debe considerar lo siguiente antes de iniciar la aplicación OLE DB:  
  
 **¿Qué implementación de programación va a utilizar para escribir una aplicación OLE DB?**  
 Microsoft ofrece varias bibliotecas para lograr esto: una biblioteca de plantillas OLE DB, OLE DB atributos y las interfaces OLE DB sin procesar en el SDK de OLE DB. Además, hay asistentes que ayudan a escribir el programa. Estas implementaciones se describen en [plantillas OLE DB, atributos y otras implementaciones](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).  
  
 **¿Tiene que escribir su propio proveedor?**  
 La mayoría de los desarrolladores no es necesario escribir su propio proveedor. Microsoft proporciona varios proveedores. Siempre que se crea una conexión de datos (por ejemplo, al agregar un consumidor al proyecto mediante el Asistente para consumidores OLE DB ATL), el **propiedades de vínculo de datos** cuadro de diálogo muestra todos los proveedores disponibles registrados en el sistema. Si uno de estos proveedores es adecuado para su propia aplicación de acceso de datos y el almacén de datos, lo más fácil es utilizar uno de ellos. Sin embargo, si el almacén de datos no se ajusta a una de estas categorías, deberá crear su propio proveedor. Para obtener información sobre la creación de proveedores, consulte [plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
 **¿Qué nivel de compatibilidad es necesario para el consumidor?**  
 Algunos consumidores pueden ser muy básicos; mientras que otros pueden ser muy complejas. La funcionalidad de objetos de OLE DB especificada por propiedades. Cuando usa el Asistente para consumidores OLE DB ATL para crear un consumidor o el Asistente para proveedores de base de datos para crear un proveedor, Establece las propiedades del objeto adecuado para usted para ofrecerle un conjunto estándar de funcionalidades. Sin embargo, si las clases de consumidor o proveedor generados por el asistente no admiten todo lo que necesita llevar a cabo, deberá hacer referencia a las interfaces de dichas clases en el [biblioteca de plantillas OLE DB](../../data/oledb/ole-db-templates.md). Estas interfaces envuelven las interfaces OLE DB sin procesar, proporcionando una implementación adicional para facilitar su uso por usted.  
  
 Por ejemplo, si desea actualizar los datos de un conjunto de filas, pero se olvidó de especificarlo cuando creó el consumidor con el asistente, puede especificar la funcionalidad después del hecho estableciendo la `DBPROP_IRowsetChange` y `DBPROP_UPDATABILITY` las propiedades del objeto de comando. A continuación, cuando se crea el conjunto de filas, tiene la `IRowsetChange` interfaz.  
  
 **¿Tiene código antiguo con otra tecnología de acceso a datos (ADO, ODBC o DAO)?**  
 Dadas las posibles combinaciones de tecnologías (por ejemplo, usar componentes de ADO con componentes de OLE DB y migrar código ODBC a OLE DB), que abarcan todas las situaciones está fuera del ámbito de la documentación de Visual C++. Sin embargo, muchos artículos que tratan diversos escenarios están disponibles en los siguientes sitios Web de Microsoft:  
  
-   [Ayuda y Soporte Técnico de Microsoft](https://support.microsoft.com/)  
  
-   [Información general de artículos técnicos de Microsoft Data Access](https://msdn.microsoft.com/en-us/library/ms810811.aspx)  
  
## <a name="see-also"></a>Vea también  
 [Programación de OLE DB](../../data/oledb/ole-db-programming.md)   
 [Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)