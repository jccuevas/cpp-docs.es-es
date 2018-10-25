---
title: Los consumidores OLE DB y proveedores | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4f52177e5fcb34470e606497297985d805a151f6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077600"
---
# <a name="ole-db-consumers-and-providers"></a>Consumidores y proveedores OLE DB

La arquitectura OLE DB usa el modelo de consumidores y proveedores. Un consumidor realiza las solicitudes de datos. Un proveedor responde a estas solicitudes mediante la colocación de datos en formato tabular y devolverla al consumidor. Cualquier llamada que puede hacer que el consumidor debe implementarse en el proveedor.

Definido técnicamente, un consumidor es cualquier código de aplicación o del sistema (no necesariamente un componente de OLE DB) que tiene acceso a datos a través de interfaces de OLE DB. Las interfaces se implementan en un proveedor. Por lo tanto, un proveedor es cualquier componente de software que implemente las interfaces OLE DB para encapsular el acceso a datos y exponerla a otros objetos (es decir, los consumidores).

Para las funciones, un consumidor llama a métodos de interfaces OLE DB; un proveedor OLE DB implementa las interfaces OLE DB necesarias.

OLE DB evita los términos cliente y servidor, porque estos roles no siempre tiene sentido, especialmente en una situación de n niveles. Dado que un consumidor puede ser un componente en un nivel que sirve a otro componente, para llamar un cliente componente sería confuso. Además, un proveedor a veces actúa más como un controlador de base de datos a un servidor.

## <a name="see-also"></a>Vea también

[Programación de OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)