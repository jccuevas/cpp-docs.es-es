---
title: Mejorar un proveedor sencillo de sólo lectura | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2018
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
ms.openlocfilehash: f798eb6219fdbc6c54e4c80474491f84f25a8060
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216479"
---
# <a name="enhancing-the-simple-read-only-provider"></a>Mejorar un proveedor sencillo de sólo lectura

Esta sección muestra cómo mejorar la [proveedor sencillo de sólo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md) creado en la sección anterior. `IRowsetLocateImpl` crea una implementación para el `IRowsetLocate` interfaz y agrega compatibilidad con marcadores.

Si dispone de un proveedor de trabajo, desea mejorarlo para implementar la actualización del proveedor, controlar transacciones o mejorar el rendimiento del algoritmo de búsqueda de filas. Mayoría de las mejoras de proveedor implica agregar una interfaz a un objeto COM existente.

El ejemplo en los temas siguientes mejora el mecanismo de captura de filas mediante la adición del `IRowsetLocate` a la interfaz `CAgentRowset`. Los temas muestran cómo para:

- [Hacer RCustomRowset herede de IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).

- [Determinar dinámicamente las columnas que se devuelven al consumidor](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Vea también

[Crear un proveedor sencillo de solo lectura](../../data/oledb/creating-a-simple-read-only-provider.md)<br/>
