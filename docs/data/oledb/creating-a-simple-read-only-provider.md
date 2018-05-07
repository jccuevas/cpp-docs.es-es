---
title: Crear un proveedor sencillo de sólo lectura | Documentos de Microsoft
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
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2662a071f443967b921c4a8db27713bc7c3e8bb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-simple-read-only-provider"></a>Crear un proveedor sencillo de sólo lectura
Una vez haya creado un proveedor de OLE DB mediante el Asistente para proyectos ATL y el Asistente para proveedores OLE DB ATL, puede agregar otra funcionalidad que desee admitir. Empezar a diseñar el proveedor mediante el examen de los tipos de datos que se va a enviar al consumidor y bajo qué condiciones. Es especialmente importante determinar si necesita admitir comandos, transacciones y otros objetos opcionales. Un buen diseño por adelantado acelerará la implementación y pruebas.  
  
 En el ejemplo se presenta en dos partes:  
  
-   La primera parte se muestra cómo [crear un proveedor sencillo de sólo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md) que lee un par de cadenas.  
  
-   La segunda parte se muestra cómo [mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md) agregando el `IRowsetLocate` interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)