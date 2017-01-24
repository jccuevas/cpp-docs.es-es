---
title: "Crear un proveedor OLE DB | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plantillas del proveedor OLE DB, crear proveedores"
  - "proveedores OLE DB, crear"
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear un proveedor OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La forma recomendada de crear un proveedor OLE DB es utilizar los asistentes para crear un proyecto COM compatible con ATL y un proveedor, y después modificar los archivos mediante las plantillas OLE DB.  Al personalizar el proveedor puede marcar como comentarios las propiedades que no desee y agregar interfaces opcionales.  
  
 Éstos son los pasos básicos:  
  
1.  Utilice el Asistente para proyectos ATL para crear los archivos básicos del proyecto y el Asistente para proveedores OLE DB ATL para crear el proveedor \(seleccione **Proveedor OLE DB ATL** en la carpeta Visual C\+\+ de **Agregar clase**\).  
  
2.  Modifique el código del método `Execute` en CMyProviderRS.h.  Encontrará un ejemplo en [Leer cadenas desde el proveedor OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).  
  
3.  Edite los mapas de propiedades que se encuentran en MyProviderDS.h, MyProviderSess.h y MyProviderRS.h.  El asistente crea mapas de propiedades que contienen todas las propiedades que un proveedor podría implementar.  Recorra los mapas de propiedades y quite o marque como comentario las propiedades para las que no es necesario que el proveedor ofrezca compatibilidad.  
  
4.  Actualice la macro PROVIDER\_COLUMN\_MAP, la cual reside en MyProviderRS.h.  Encontrará un ejemplo en [Almacenar cadenas en el proveedor OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).  
  
5.  Cuando esté preparado para probar el proveedor, puede intentar buscarlo en la lista de proveedores.  Si desea consultar ejemplos de código de prueba que busquen un proveedor en una lista, vea los ejemplos [CATDB](http://msdn.microsoft.com/es-es/003d516b-2bf6-444e-8be5-4ebaa0b66046) y [DBVIEWER](http://msdn.microsoft.com/es-es/07620f99-c347-4d09-9ebc-2459e8049832), o el ejemplo de [Implementar un consumidor simple](../../data/oledb/implementing-a-simple-consumer.md).  
  
6.  Agregue las interfaces adicionales que desee.  Vea el ejemplo de [Mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
    > [!NOTE]
    >  De manera predeterminada, los asistentes generan código compatible con el nivel 0 de OLE DB.  Para asegurarse de que la aplicación mantiene la compatibilidad con el nivel 0, no quite del código ninguna de las interfaces generadas por el asistente.  
  
## Vea también  
 [CATDB](http://msdn.microsoft.com/es-es/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/es-es/07620f99-c347-4d09-9ebc-2459e8049832)