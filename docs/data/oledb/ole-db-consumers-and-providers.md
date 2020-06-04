---
title: Consumidores y proveedores OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
ms.openlocfilehash: d57ded9d084971c3562fc7f22e6a1a12a4e3368d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210086"
---
# <a name="ole-db-consumers-and-providers"></a>Consumidores y proveedores OLE DB

La arquitectura de OLE DB utiliza el modelo de consumidores y proveedores. Un consumidor realiza solicitudes de datos. Un proveedor responde a estas solicitudes colocando los datos en formato tabular y devolviendo al consumidor. Cualquier llamada que pueda realizar el consumidor debe implementarse en el proveedor.

Técnicamente definido, un consumidor es cualquier código de sistema o de aplicación (no necesariamente un componente OLE DB) que tiene acceso a los datos a través de interfaces OLE DB. Las interfaces se implementan en un proveedor. Por lo tanto, un proveedor es cualquier componente de software que implementa interfaces OLE DB para encapsular el acceso a los datos y exponerlo a otros objetos (es decir, consumidores).

En el caso de los roles, un consumidor llama a métodos en interfaces de OLE DB; un proveedor de OLE DB implementa las interfaces de OLE DB necesarias.

OLE DB evita los términos cliente y servidor, ya que estos roles no siempre tienen sentido, especialmente en una situación de n niveles. Dado que un consumidor podría ser un componente de un nivel que sirve a otro componente, para llamarlo un componente de cliente sería confuso. Además, a veces un proveedor actúa más como un controlador de base de datos que un servidor de.

## <a name="see-also"></a>Consulte también

[Programación de OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)
