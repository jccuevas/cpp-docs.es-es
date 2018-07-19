---
title: Mejorar un proveedor sencillo de sólo lectura | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c88714e4e1651839cdc5fd4b92d3c5222aa08d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100023"
---
# <a name="enhancing-the-simple-read-only-provider"></a>Mejorar un proveedor sencillo de sólo lectura
Esta sección muestra cómo mejorar la [proveedor sencillo de sólo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md) creado en la sección anterior. `IRowsetLocateImpl` crea una implementación para el `IRowsetLocate` de interfaz y agrega compatibilidad con marcadores.  
  
 Cuando tenga un proveedor en funcionamiento, puede mejorarlo para implementar la actualización del proveedor, controlar transacciones o mejorar el rendimiento del algoritmo de obtención de filas. Muchas de estas mejoras de proveedor implican agregar una interfaz a un objeto COM existente.  
  
 El ejemplo en los temas siguientes mejora el mecanismo de captura de filas mediante la adición de la `IRowsetLocate` a la interfaz `CAgentRowset`. Los temas muestran cómo para:  
  
-   [Hacer que RMyProviderRowset herede de IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).  
  
-   [Determinar dinámicamente las columnas que se devuelven al consumidor](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Vea también  
 [Crear un proveedor sencillo de solo lectura](../../data/oledb/creating-a-simple-read-only-provider.md)