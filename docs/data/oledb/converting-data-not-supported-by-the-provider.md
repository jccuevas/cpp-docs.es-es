---
title: Convertir datos no compatibles con el proveedor
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e87aebc4d6f23343af9a2f966d2c522e95b304ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211502"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Convertir datos no compatibles con el proveedor

Cuando el consumidor solicita un tipo de datos no admitido por el proveedor, el código de plantilla de proveedor de OLE DB para `IRowsetImpl::GetData` llama a msdadc. dll para convertir el tipo de datos.

Si implementa una interfaz como `IRowsetChange` que requiere la conversión de datos, puede llamar a MSDAENUM. dll para realizar la conversión. Use `GetData`, que se define en atldb. h, como ejemplo.

## <a name="see-also"></a>Consulte también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
