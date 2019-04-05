---
title: Información general sobre la programación de OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: 68ada06514defe0f7f5332288ad8e91a7d8d9351
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035535"
---
# <a name="ole-db-programming-overview"></a>Información general sobre la programación de OLE DB

OLE DB es una tecnología de base de datos de alto rendimiento basado en COM. Proporciona una manera común de obtener acceso a datos independientemente de la forma en que se almacenan. En una situación típica de negocios, una gran cantidad de información no se almacena en bases de datos corporativas. Esta información se halla en sistemas de archivos (FAT o NTFS, por ejemplo), archivos secuenciales indizados, bases de datos personales (como Access), hojas de cálculo (como Excel), aplicaciones de planeación de proyectos (como Project) y correo electrónico (como Outlook). OLE DB permite tener acceso a cualquier tipo de almacén de datos de la misma manera, siempre que el almacén de datos tenga un proveedor OLE DB.

OLE DB permite desarrollar aplicaciones que tienen acceso a diversos orígenes de datos, tanto si son DBMS o no. OLE DB hace posible el acceso universal a datos mediante interfaces COM compatibles con la funcionalidad DBMS de un origen de datos determinado. COM reduce la duplicación innecesaria de servicios y proporciona interoperabilidad máxima, no sólo entre orígenes de datos, sino también entre otras aplicaciones.

## <a name="benefits-of-com"></a>Ventajas de COM

Aquí es donde entra en juego COM. OLE DB es un conjunto de interfaces COM. Al obtener acceso a los datos a través de un conjunto uniforme de interfaces, se puede organizar una base de datos en una matriz de componentes cooperativos.

Basado en la especificación COM, OLE DB define una colección ampliable y mantenible de interfaces que extienden y encapsulan partes coherentes y reutilizables de la funcionalidad DBMS. Estas interfaces definen los límites de componentes DBMS como contenedores de filas, procesadores de consultas y coordinadores de transacciones, que permiten el acceso transaccional uniforme a diversos orígenes de información.

## <a name="see-also"></a>Vea también

[Programación de OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[plantillas OLE DB](../../data/oledb/ole-db-templates.md)