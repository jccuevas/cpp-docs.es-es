---
title: Habilitar y deshabilitar servicios para un proveedor | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ef36e35234aa4878e30e70748a5b2ba2975c38dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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