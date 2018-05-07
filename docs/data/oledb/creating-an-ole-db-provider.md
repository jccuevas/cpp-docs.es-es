---
title: Crear un proveedor OLE DB | Documentos de Microsoft
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
ms.openlocfilehash: f649b5b4c79c4148d0aed026b044485ca2b1eaa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="creating-an-ole-db-provider"></a>Crear un proveedor OLE DB
La manera recomendada para crear un proveedor OLE DB es usar los asistentes para crear un proyecto ATL COM y un proveedor y, a continuación, modificar los archivos mediante las plantillas OLE DB. Mientras personaliza el proveedor, puede Comente propiedades que no desee y agregar interfaces opcionales.  
  
 Estos son los pasos básicos:  
  
1.  Usar el Asistente para proyectos ATL para crear los archivos básicos del proyecto y el Asistente para proveedores OLE DB ATL para crear el proveedor (seleccione **proveedor OLE DB ATL** desde la carpeta de Visual C++ en **Agregar clase**).  
  
2.  Modificar el código en el `Execute` método en CMyProviderRS.h. Para obtener un ejemplo, vea [leer cadenas en el proveedor OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).  
  
3.  Editar las asignaciones de propiedad en MyProviderDS.h, MyProviderSess.h y MyProviderRS.h. El asistente crea mapas de propiedades que contienen todas las propiedades que puede implementar un proveedor. Vaya a través de los mapas de propiedades y quite o tu comentario las propiedades que no es necesario que el proveedor admite.  
  
4.  Actualice la macro PROVIDER_COLUMN_MAP, que se encuentra en MyProviderRS.h. Para obtener un ejemplo, vea [almacenar cadenas en el proveedor OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).  
  
5.  Cuando esté listo para probar el proveedor, puede probarlo, intentando encontrar el proveedor de una enumeración de proveedor. Para obtener ejemplos de código de prueba que busquen un proveedor en una enumeración, consulte la [CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046) y [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) muestras o en el ejemplo de [implementar un consumidor Simple](../../data/oledb/implementing-a-simple-consumer.md).  
  
6.  Agregue las interfaces adicionales que desee. Para obtener un ejemplo, vea [mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
    > [!NOTE]
    >  De forma predeterminada, los asistentes generan código que es el nivel 0 compatibles con OLE DB. Para asegurarse de que la aplicación siga siendo el nivel 0 compatible, no quite cualquiera de las interfaces generadas por el asistente desde el código.  
  
## <a name="see-also"></a>Vea también  
 [CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)