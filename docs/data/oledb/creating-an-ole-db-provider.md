---
title: Creación de un proveedor OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 10/13/2018
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
ms.openlocfilehash: 225f27703ff56c4b37bad4287a708df7a2b1f479
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410725"
---
# <a name="creating-an-ole-db-provider"></a>Crear un proveedor OLE DB

La manera recomendada para crear un proveedor OLE DB es usar a los asistentes para crear un proyecto ATL COM y un proveedor y, a continuación, modificar los archivos mediante las plantillas OLE DB. Para personalizar su proveedor, puede comentar las propiedades no deseadas y agregar interfaces opcionales.  
  
Estos son los pasos básicos:  

1. Use la **Asistente para proyectos ATL** para crear los archivos de proyecto básico y **Asistente para proveedores OLE DB de ATL** para crear el proveedor (seleccione **proveedor OLEDB ATL** desde el **Instalado** > **Visual C++** > **ATL** carpeta **Agregar nuevo elemento**).  

   > [!NOTE]
   > El proyecto debe incluir compatibilidad con MFC antes de agregar un **proveedor OLEDB ATL**.
  
1. Modifique el código en el `Execute` método [CMyProviderRowset(MyProviderRS.h)](cmyproviderrowset-myproviderrs-h.md). Para obtener un ejemplo, vea [leer cadenas en el proveedor OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).  
  
1. Editar la propiedad se asigna en [MyProviderDS.h](cmyprovidersource-myproviderds-h.md), [MyProviderSess.h](cmyprovidersession-myprovidersess-h.md), y [MyProviderRS.h](cmyproviderrowset-myproviderrs-h.md). El asistente crea los mapas de propiedades que contienen todas las propiedades que se podría implementar un proveedor. Vaya a través de los mapas de propiedades y quite o comente las propiedades que no es necesario que su proveedor de soporte técnico.  
  
1. Actualizar PROVIDER_COLUMN_MAP, que puede encontrarse en [CMyProviderRowset(MyProviderRS.h)](cmyproviderrowset-myproviderrs-h.md). Para obtener un ejemplo, vea [almacenar cadenas en el proveedor OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).  
  
1. Cuando esté listo para probar el proveedor, puede probarla mediante tratando de encontrar el proveedor de una enumeración de proveedor. Para obtener ejemplos de código de prueba que busquen un proveedor en una enumeración, vea el [CATDB](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb) y [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) ejemplos o en el ejemplo de [implementar un consumidor sencillo](../../data/oledb/implementing-a-simple-consumer.md).  
  
1. Agregue las interfaces adicionales que desee. Para obtener un ejemplo, vea [mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
   > [!NOTE]
   > De forma predeterminada, los asistentes generan código que es el nivel 0 compatible con OLE DB. Para asegurarse de que la aplicación sigue siendo el nivel 0 compatible, no quite ninguna de las interfaces generados por el asistente desde el código.  
  
## <a name="see-also"></a>Vea también  

[Ejemplo CatDB: Explorador de esquemas de origen de datos](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)<br/>
[Ejemplo DBViewer: Explorador de base de datos](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)
