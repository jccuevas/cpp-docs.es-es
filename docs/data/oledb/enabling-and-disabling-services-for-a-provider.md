---
title: Habilitar y deshabilitar servicios para un proveedor | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dc6b3d7cc8e80eaa24c2e2dd9b4e23e79dfb09f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Habilitar y deshabilitar servicios para un proveedor
Servicios OLE DB individuales pueden ser habilitados o deshabilitados de forma predeterminada para todas las aplicaciones que tienen acceso a un único proveedor. Esto se realiza agregando un **OLEDB_SERVICES** entrada del registro con el proveedor del CLSID, con un `DWORD` valor que especifica los servicios para habilitar o deshabilitar, como se muestra en la tabla siguiente.  
  
|Servicios predeterminados habilitados|Valor de palabra clave|  
|------------------------------|-------------------|  
|Todos los servicios (valor predeterminado)|0xFFFFFFFF|  
|Todas excepto Pooling y AutoEnlistment|0xFFFFFFFE|  
|Todos los servicios excepto Client Cursor|0xfffffffb|  
|Todos excepto Pooling, AutoEnlistment y Cursor de cliente|0xfffffff0|  
|No hay servicios|0x00000000|  
|Ninguna agregación, todos los servicios deshabilitados|\<Falta una clave >|  
  
## <a name="see-also"></a>Vea también  
 [Habilitar y deshabilitar servicios OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)