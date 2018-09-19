---
title: Habilitar y deshabilitar servicios para un proveedor | Microsoft Docs
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
ms.openlocfilehash: a5db612c836e4b902e7cad83017661246f4b649e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079393"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Habilitar y deshabilitar servicios para un proveedor

Servicios OLE DB individuales pueden ser habilitados o deshabilitados de forma predeterminada para todas las aplicaciones que tienen acceso a un único proveedor. Esto se realiza mediante la adición de una entrada de registro OLEDB_SERVICES bajo el CLSID del proveedor, con un `DWORD` valor que especifica los servicios para habilitar o deshabilitar, como se muestra en la tabla siguiente.  
  
|Servicios predeterminados habilitados|Valor de palabra clave|  
|------------------------------|-------------------|  
|Todos los servicios (valor predeterminado)|0xFFFFFFFF|  
|Todos excepto la agrupación y AutoEnlistment|0xFFFFFFFE|  
|Todos excepto el Cursor de cliente|0xfffffffb|  
|Todos excepto Pooling, AutoEnlistment y Cursor de cliente|0xfffffff0|  
|No hay servicios|0x00000000|  
|Ninguna agregación, todos los servicios deshabilitados|\<Falta la clave >|  
  
## <a name="see-also"></a>Vea también  

[Habilitar y deshabilitar servicios OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)