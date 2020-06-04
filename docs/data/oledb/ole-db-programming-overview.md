---
title: Información general sobre la programación de OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: 2b855e0917ba9cdbdaa38a92473d7bddb4279101
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210079"
---
# <a name="ole-db-programming-overview"></a>Información general sobre la programación de OLE DB

OLE DB es una tecnología de base de datos basada en COM de alto rendimiento. Proporciona una forma común de obtener acceso a los datos independientes del formulario en el que se almacenan. En una situación empresarial típica, una gran cantidad de información no se almacena en las bases de datos corporativas. Esta información se halla en sistemas de archivos (FAT o NTFS, por ejemplo), archivos secuenciales indizados, bases de datos personales (como Access), hojas de cálculo (como Excel), aplicaciones de planeación de proyectos (como Project) y correo electrónico (como Outlook). OLE DB permite tener acceso a cualquier tipo de almacén de datos de la misma manera, siempre que el almacén de datos tenga un proveedor OLE DB.

OLE DB permite desarrollar aplicaciones que tienen acceso a diversos orígenes de datos, tanto si son DBMS como si no. OLE DB hace posible el acceso universal a datos mediante interfaces COM compatibles con la funcionalidad DBMS de un origen de datos determinado. COM reduce la duplicación innecesaria de servicios y proporciona interoperabilidad máxima, no sólo entre orígenes de datos, sino también entre otras aplicaciones.

## <a name="benefits-of-com"></a>Ventajas de COM

Aquí es donde entra en juego COM. OLE DB es un conjunto de interfaces COM. Al obtener acceso a los datos a través de un conjunto uniforme de interfaces, se puede organizar una base de datos en una matriz de componentes cooperativos.

Basado en la especificación COM, OLE DB define una colección ampliable y mantenible de interfaces que extienden y encapsulan partes coherentes y reutilizables de la funcionalidad DBMS. Estas interfaces definen los límites de componentes DBMS como contenedores de filas, procesadores de consultas y coordinadores de transacciones, que permiten el acceso transaccional uniforme a diversos orígenes de información.

## <a name="see-also"></a>Consulte también

[Programación de OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Plantillas OLE DB](../../data/oledb/ole-db-templates.md)
