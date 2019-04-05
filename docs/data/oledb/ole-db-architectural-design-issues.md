---
title: Cuestiones de diseño de arquitectura OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: 2f0a7a114c671e17d8f95280ab00ed93570e8609
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037677"
---
# <a name="ole-db-architectural-design-issues"></a>Cuestiones de diseño de arquitectura OLE DB

Antes de iniciar la aplicación OLE DB, tenga en cuenta lo siguiente:

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>¿Qué implementación de programación va a utilizar para escribir una aplicación OLE DB?

Microsoft ofrece varias bibliotecas para realizar esta tarea: una biblioteca de plantillas OLE DB, OLE DB atributos y las interfaces OLE DB sin procesar en el SDK de OLE DB. Además, hay asistentes que ayudan a escribir el programa. Estas implementaciones se describen en [plantillas OLE DB, atributos y otras implementaciones](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).

## <a name="do-you-need-to-write-your-own-provider"></a>¿Tiene que escribir su propio proveedor?

La mayoría de los desarrolladores no es necesario escribir su propio proveedor. Microsoft proporciona varios proveedores. Siempre que se crea una conexión de datos (por ejemplo, al agregar un consumidor al proyecto mediante el **el Asistente para consumidores OLE DB ATL**), el **propiedades de vínculo de datos** cuadro de diálogo muestra todos los proveedores disponibles registrado en el sistema. Si uno de los proveedores es adecuado para su propia aplicación de acceso de datos y el almacén de datos, lo más fácil es usar uno de ellos. Sin embargo, si el almacén de datos no ajusta una de estas categorías, deberá crear su propio proveedor. Para obtener información sobre la creación de proveedores, consulte [plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>¿Qué nivel de compatibilidad es necesario para el consumidor?

Algunos consumidores pueden ser básicos; mientras que otros pueden ser complejos. La funcionalidad de objetos de OLE DB especificada por propiedades. Cuando se usa el **el Asistente para consumidores OLE DB ATL** para crear un consumidor o el **Asistente para la base de datos de proveedor** para crear un proveedor, Establece las propiedades de objeto adecuado para usted para ofrecerle un conjunto estándar de funcionalidades. Sin embargo, si las clases de consumidor o proveedor generados por el asistente no admiten todo lo que necesita llevar a cabo, deberá hacer referencia a las interfaces de dichas clases en el [biblioteca de plantillas OLE DB](../../data/oledb/ole-db-templates.md). Estas interfaces envuelven las interfaces OLE DB sin procesar, proporcionando una implementación adicional para facilitar su uso por usted.

Por ejemplo, si desea actualizar los datos de un conjunto de filas, pero se olvidó de especificarlo cuando creó el consumidor con el asistente, puede especificar la funcionalidad después del hecho estableciendo la `DBPROP_IRowsetChange` y `DBPROP_UPDATABILITY` las propiedades del objeto de comando. A continuación, cuando se crea el conjunto de filas, tiene la `IRowsetChange` interfaz.

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>¿Tiene código antiguo con otra tecnología de acceso a datos (ADO, ODBC o DAO)?

Dadas las posibles combinaciones de tecnologías (por ejemplo, usar componentes de ADO con componentes de OLE DB y migrar código ODBC a OLE DB), que abarcan todas las situaciones está fuera del ámbito de la documentación de Visual C++. Sin embargo, existen muchos artículos que abarcan varios escenarios en los siguientes sitios web de Microsoft:

- [Ayuda y soporte técnico](https://support.microsoft.com/)

- [Información general de artículos técnicos de Microsoft Data Access](https://msdn.microsoft.com/library/ms810811.aspx)

## <a name="see-also"></a>Vea también

[Programación de OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)
