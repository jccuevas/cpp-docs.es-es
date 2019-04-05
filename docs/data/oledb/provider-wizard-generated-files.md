---
title: Archivos generados por el Asistente para proveedores
ms.date: 10/18/2018
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: a9a706463326249135a55bc907cb8a664a3ca808
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037096"
---
# <a name="provider-wizard-generated-files"></a>Archivos generados por el Asistente para proveedores

El **el Asistente para proveedores OLE DB ATL** genera los siguientes archivos. Los temas siguientes utilizan el nombre corto *personalizado*, pero los nombres de archivo exacto dependen de la elección realizada cuando se crea el proveedor.

|Nombre del archivo|Descripción|
|---------------|-----------------|
|*Custom*RS.cpp|Contiene la aplicación auxiliar de comando `Execute` método y el mapa de columnas del proveedor.|
|*Custom*DS.h|Implementa el objeto de origen de datos. Este archivo de encabezado contiene la asignación de propiedad para propiedades del origen de datos.|
|*Custom*RS.h|Implementa los objetos de comando y conjunto de filas. Este archivo de encabezado contiene la asignación de propiedad para las propiedades del conjunto de filas y el comando.|
|*Custom*Sess.h|Implementa el objeto de sesión. Este archivo de encabezado contiene la asignación de propiedad para propiedades de la sesión.|
|*Custom*.rgs|Contiene los objetos registrados generados por el **Asistente para proveedores OLE DB**.|

## <a name="see-also"></a>Vea también

[Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
