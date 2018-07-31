---
title: Información general de programación de OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 735e753412498d3285ad26e02b017fb931960daf
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336899"
---
# <a name="ole-db-programming-overview"></a>Información general sobre la programación de OLE DB
OLE DB es una tecnología de base de datos de alto rendimiento basado en COM. Proporciona una manera común de acceder a los datos independientemente de la forma en que se almacenan. En una situación típica de negocios, una gran cantidad de información se almacena fuera de las bases de datos corporativas. Esta información se halla en sistemas de archivos (FAT o NTFS, por ejemplo), archivos secuenciales indizados, bases de datos personales (como Access), hojas de cálculo (como Excel), aplicaciones de planeación de proyectos (como Project) y correo electrónico (como Outlook). OLE DB permite tener acceso a cualquier tipo de almacén de datos de la misma manera, siempre que el almacén de datos tenga un proveedor OLE DB.
  
 OLE DB permite desarrollar aplicaciones que obtienen acceso a diversos orígenes de datos, tanto si son DBMS como si no lo son. OLE DB hace posible el acceso universal a datos mediante interfaces COM compatibles con la funcionalidad DBMS de un origen de datos determinado. COM reduce la duplicación innecesaria de servicios y proporciona interoperabilidad máxima, no sólo entre orígenes de datos, sino también entre otras aplicaciones.  
  
## <a name="benefits-of-com"></a>Ventajas de COM  
 Aquí es donde entra en juego COM. OLE DB es un conjunto de interfaces COM. Al obtener acceso a los datos a través de un conjunto uniforme de interfaces, se puede organizar una base de datos en una matriz de componentes cooperativos.  
  
 Basado en la especificación COM, OLE DB define una colección ampliable y mantenible de interfaces que extienden y encapsulan partes coherentes y reutilizables de la funcionalidad DBMS. Estas interfaces definen los límites de componentes DBMS como contenedores de filas, procesadores de consultas y coordinadores de transacciones, que permiten el acceso transaccional uniforme a diversos orígenes de información.  
 
## <a name="see-also"></a>Vea también  
 [Programación de OLE DB](../../data/oledb/ole-db-programming.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Plantillas OLE DB](../../data/oledb/ole-db-templates.md)