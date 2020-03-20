---
title: Cuestiones de diseño de arquitectura OLE DB
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: b481d9948d3055247bd284ca794a0fa65905e21b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544553"
---
# <a name="ole-db-architectural-design-issues"></a>Cuestiones de diseño de arquitectura OLE DB

> [!NOTE]
> El Asistente para proveedores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores. Puede seguir agregando la funcionalidad manualmente. Para obtener más información, consulte [Crear un consumidor sin utilizar un asistente](creating-a-consumer-without-using-a-wizard.md).

Antes de iniciar la aplicación OLE DB, tenga en cuenta lo siguiente:

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>¿Qué implementación de programación va a utilizar para escribir una aplicación OLE DB?

Microsoft ofrece varias bibliotecas para realizar esta tarea: una biblioteca de plantillas OLE DB, atributos OLE DB y las interfaces OLE DB sin procesar del SDK de OLE DB. Además, hay asistentes que ayudan a escribir el programa. Estas implementaciones se describen en [Plantillas, atributos y otras implementaciones de OLE DB](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).

## <a name="do-you-need-to-write-your-own-provider"></a>¿Tiene que escribir su propio proveedor?

La mayoría de los desarrolladores no tienen que escribir su propio proveedor. Microsoft proporciona varios proveedores. Siempre que se crea una conexión de datos (por ejemplo, al agregar un consumidor al proyecto mediante el **Asistente para consumidores OLE DB ATL**), el cuadro de diálogo **Propiedades de vínculo de datos** muestra todos los proveedores disponibles registrado en el sistema. Si uno de los proveedores es adecuado para su propia aplicación de acceso de datos y almacén de datos, lo más fácil es usar uno de ellos. Sin embargo, si el almacén de datos no se ajusta a una de estas categorías, deberá crear su propio proveedor. Para obtener información sobre la creación de proveedores, consulte [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>¿Qué nivel de compatibilidad es necesario para el consumidor?

Algunos consumidores pueden ser básicos; mientras que otros pueden ser complejos. La funcionalidad de objetos OLE DB se especifica mediante propiedades. Cuando se usa el **Asistente para consumidores OLE DB ATL** para crear un consumidor o el **Asistente para la base de datos de proveedor** con el fin de crear un proveedor, establece las propiedades de objeto adecuado para usted para ofrecerle un conjunto estándar de funcionalidades. Sin embargo, si las clases de consumidor o proveedor generados por el asistente no admiten todo lo que necesita llevar a cabo, deberá hacer referencia a las interfaces de dichas clases en la [biblioteca de plantillas OLE DB](../../data/oledb/ole-db-templates.md). Estas interfaces envuelven las interfaces OLE DB sin procesar, lo que proporciona una implementación adicional para facilitar su uso.

Por ejemplo, si desea actualizar los datos de un conjunto de filas, pero se olvidó de especificarlo cuando creó el consumidor con el asistente, puede especificar la funcionalidad después del hecho estableciendo las propiedades `DBPROP_IRowsetChange` y `DBPROP_UPDATABILITY` del objeto de comando. A continuación, cuando se crea el conjunto de filas, tiene la interfaz `IRowsetChange`.

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>¿Tiene código antiguo con otra tecnología de acceso a datos (ADO, ODBC o DAO)?

Dadas las posibles combinaciones de tecnologías (por ejemplo, usar componentes ADO con componentes OLE DB y migrar código ODBC a OLE DB), abarcar todas las situaciones queda fuera del ámbito de la documentación de Visual C++. Sin embargo, existen muchos artículos que abarcan varios escenarios en los siguientes sitios web de Microsoft:

- [Ayuda y soporte técnico de Microsoft](https://support.microsoft.com/)

- [Introducción a artículos técnicos de Microsoft Data Access](/previous-versions/ms810811(v=msdn.10))

## <a name="see-also"></a>Consulte también

[Programación de OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)
