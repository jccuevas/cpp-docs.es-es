---
title: Convertir datos no compatibles con el proveedor
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: a53781f71a55dfb07dc996e5e25644d9337e4c63
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473449"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Convertir datos no compatibles con el proveedor

Cuando el consumidor solicita un tipo de datos que no es compatible con el proveedor, el código para la plantilla de proveedores OLE DB `IRowsetImpl::GetData` llama a Msdadc.dll para convertir el tipo de datos.

Si implementa una interfaz como `IRowsetChange` que requiere conversión de datos, puede llamar a Msdaenum.dll para realizar la conversión. Use `GetData`, definido en Atldb.h, por ejemplo.

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)