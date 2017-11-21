---
title: Los consumidores OLE DB y proveedores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd09e1566a6f53244d420387870a03b0b34f8fb6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-consumers-and-providers"></a>Consumidores y proveedores OLE DB
La arquitectura OLE DB usa el modelo de consumidores y proveedores. Un consumidor realiza las solicitudes de datos. Un proveedor responde a estas solicitudes al colocar los datos en formato tabular y devolverlo al consumidor. Cualquier llamada que puede hacer que el consumidor debe implementarse en el proveedor.  
  
 Técnicamente, un consumidor es cualquier código de aplicación o del sistema (no necesariamente un componente de OLE DB) que tiene acceso a datos a través de interfaces de OLE DB. Las interfaces se implementan en un proveedor. Por lo tanto, un proveedor es cualquier componente de software que implementa las interfaces OLE DB para encapsular el acceso a datos y exponerlo a otros objetos (es decir, los consumidores).  
  
 En términos de funciones, un consumidor llama a métodos de interfaces OLE DB; un proveedor OLE DB implementa las interfaces OLE DB necesarias.  
  
 OLE DB evita los términos cliente y servidor porque estas funciones no siempre tienen sentido, especialmente en una situación de n niveles. Dado que un consumidor puede ser un componente en un nivel que sirve a otro componente, para llamar a un cliente componente sería confuso. Además, un proveedor a veces actúa más como un controlador de base de datos de un servidor.  
  
## <a name="see-also"></a>Vea también  
 [Programación de OLE DB](../../data/oledb/ole-db-programming.md)   
 [Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)