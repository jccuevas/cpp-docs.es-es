---
title: Archivos generados por el Asistente para proveedores
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: 0638680482546f56f26b70660ab43bd9848438a3
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707486"
---
# <a name="provider-wizard-generated-files"></a>Archivos generados por el Asistente para proveedores

::: moniker range="vs-2019"

El Asistente para proveedores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

El **Asistente para proveedores OLE DB ATL** genera los siguientes archivos. Los temas siguientes utilizan el nombre corto *Personalizado*, pero los nombres de archivo exacto dependen de la elección realizada cuando se crea el proveedor.

|Nombre del archivo|Descripción|
|---------------|-----------------|
|*Custom*RS.cpp|Contiene el método `Execute` del asistente de comando y la asignación de columnas del proveedor.|
|*Custom*DS.h|Implementa el objeto de origen de datos. Este archivo de encabezado contiene la asignación de propiedades para las propiedades del origen de datos.|
|*Custom*RS.h|Implementa los objetos de comando y conjunto de filas. Este archivo de encabezado contiene la asignación de propiedades para las propiedades del conjunto de filas y comando.|
|*Custom*Sess.h|Implementa el objeto de sesión. Este archivo de encabezado contiene la asignación de propiedades para las propiedades de sesión.|
|*Custom*.rgs|Contiene los objetos registrados generados por el **Asistente para proveedores OLE DB**.|

::: moniker-end

## <a name="see-also"></a>Vea también

[Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
