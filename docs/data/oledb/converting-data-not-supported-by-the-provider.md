---
title: Convertir datos no compatibles con el proveedor
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e60f6cd4f7dca1ed3e176cabefc42f69946436a4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033844"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Convertir datos no compatibles con el proveedor

Cuando el consumidor solicita un tipo de datos que no es compatible con el proveedor, el código para la plantilla de proveedores OLE DB `IRowsetImpl::GetData` llama a Msdadc.dll para convertir el tipo de datos.

Si implementa una interfaz como `IRowsetChange` que requiere conversión de datos, puede llamar a Msdaenum.dll para realizar la conversión. Use `GetData`, definido en Atldb.h, por ejemplo.

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)