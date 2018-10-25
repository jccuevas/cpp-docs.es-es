---
title: Convertir datos no compatibles con el proveedor | Microsoft Docs
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
ms.openlocfilehash: 79889125675a3e544802eb700718dee0829457c5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066128"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Convertir datos no compatibles con el proveedor

Cuando el consumidor solicita un tipo de datos que no es compatible con el proveedor, el código para la plantilla de proveedores OLE DB `IRowsetImpl::GetData` llama a Msdadc.dll para convertir el tipo de datos.

Si implementa una interfaz como `IRowsetChange` que requiere conversión de datos, puede llamar a Msdaenum.dll para realizar la conversión. Use `GetData`, definido en Atldb.h, por ejemplo.

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)