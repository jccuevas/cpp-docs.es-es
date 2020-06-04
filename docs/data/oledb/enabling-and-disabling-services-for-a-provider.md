---
title: Habilitar y deshabilitar servicios para un proveedor
ms.date: 07/30/2019
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: a74f8a8b099a30cf25007547e8059c77728435f9
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2019
ms.locfileid: "79544463"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Habilitar y deshabilitar servicios para un proveedor

Los servicios de OLE DB individuales se pueden habilitar o deshabilitar de forma predeterminada para todas las aplicaciones que tienen acceso a un solo proveedor. Para ello, se agrega una entrada de registro de OLEDB_SERVICES en el CLSID del proveedor, con un valor DWORD que especifica los servicios que se van a habilitar o deshabilitar, tal como se muestra en la tabla siguiente.

|Servicios predeterminados habilitados|Valor DWORD|
|------------------------------|-------------------|
|Todos los servicios excepto el cursor y la agrupación del cliente|0xfffffffa|
|Todos los servicios excepto el cursor del cliente|0xfffffffb|
|Todos los servicios excepto la agrupación y la inscripción automática|0xfffffffc|
|Todos los servicios excepto la agrupación|0xfffffffe|
|Todos los servicios (valor predeterminado)|0xffffffff|
|Sin servicios|0x00000000|
|Sin agregación, todos los servicios deshabilitados|No hay ninguna entrada del registro OLEDB_Services|

## <a name="see-also"></a>Consulte también

[Habilitar y deshabilitar servicios OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)
