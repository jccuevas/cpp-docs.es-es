---
title: Convertir datos no compatibles con el proveedor | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d0be19345ff6c425cfbc020f2096ca82680586d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095471"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Convertir datos no compatibles con el proveedor
Cuando el consumidor solicita un tipo de datos que no es compatible con el proveedor, el código de la plantilla de proveedores OLE DB para `IRowsetImpl::GetData` llama a Msdadc.dll para convertir el tipo de datos.  
  
 Si implementa una interfaz como `IRowsetChange` que requiere conversión de datos, puede llamar a Msdaenum.dll para realizar la conversión. Use `GetData`, definido en Atldb.h, por ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)