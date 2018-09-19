---
title: Creación de un proveedor OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 441fdfcf98e08b30e1049cac986ebc9e0f7df682
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030409"
---
# <a name="creating-an-ole-db-provider"></a>Crear un proveedor OLE DB

La manera recomendada para crear un proveedor OLE DB es usar a los asistentes para crear un proyecto ATL COM y un proveedor y, a continuación, modificar los archivos mediante las plantillas OLE DB. Para personalizar su proveedor, puede comentar las propiedades no deseadas y agregar interfaces opcionales.  
  
Estos son los pasos básicos:  
  
1. Usar el Asistente para proyectos ATL para crear los archivos de proyecto básico y el Asistente para proveedores OLE DB ATL para crear el proveedor (seleccione **proveedor OLE DB ATL** desde la carpeta de Visual C++ en **Agregar clase**).  
  
1. Modifique el código en el `Execute` método CMyProviderRS.h. Para obtener un ejemplo, vea [leer cadenas en el proveedor OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).  
  
1. Editar las asignaciones de propiedad en MyProviderDS.h, MyProviderSess.h y MyProviderRS.h. El asistente crea los mapas de propiedades que contienen todas las propiedades que se podría implementar un proveedor. Vaya a través de los mapas de propiedades y quite o comente las propiedades que no es necesario que su proveedor de soporte técnico.  
  
1. Actualice PROVIDER_COLUMN_MAP, que puede encontrarse en MyProviderRS.h. Para obtener un ejemplo, vea [almacenar cadenas en el proveedor OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).  
  
1. Cuando esté listo para probar el proveedor, puede probarla mediante tratando de encontrar el proveedor de una enumeración de proveedor. Para obtener ejemplos de código de prueba que busquen un proveedor en una enumeración, vea el [CATDB](https://github.com/Microsoft/VCSamples) y [DBVIEWER](https://github.com/Microsoft/VCSamples) ejemplos o en el ejemplo de [implementar un consumidor sencillo](../../data/oledb/implementing-a-simple-consumer.md).  
  
1. Agregue las interfaces adicionales que desee. Para obtener un ejemplo, vea [mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
    > [!NOTE]
    >  De forma predeterminada, los asistentes generan código que es el nivel 0 compatible con OLE DB. Para asegurarse de que la aplicación sigue siendo el nivel 0 compatible, no quite ninguna de las interfaces generados por el asistente desde el código.  
  
## <a name="see-also"></a>Vea también  

[CATDB](https://github.com/Microsoft/VCSamples)<br/>
[DBVIEWER](https://github.com/Microsoft/VCSamples)