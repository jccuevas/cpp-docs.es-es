---
title: Habilitar y deshabilitar servicios para un proveedor
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: d91f08accf1a8be69f63d6bbcaa4c620d68c1077
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175455"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Habilitar y deshabilitar servicios para un proveedor

Servicios OLE DB individuales pueden ser habilitados o deshabilitados de forma predeterminada para todas las aplicaciones que tienen acceso a un único proveedor. Esto se realiza mediante la adición de una entrada de registro OLEDB_SERVICES bajo el CLSID del proveedor, con un valor DWORD que especifica los servicios para habilitar o deshabilitar, como se muestra en la tabla siguiente.

|Servicios predeterminados habilitados|Valor de palabra clave|
|------------------------------|-------------------|
|Todos los servicios (valor predeterminado)|0xffffffff|
|Todos excepto la agrupación y AutoEnlistment|0xfffffffe|
|Todos excepto el Cursor de cliente|0xfffffffb|
|Todos excepto Pooling, AutoEnlistment y Cursor de cliente|0xfffffff0|
|No hay servicios|0x00000000|
|Ninguna agregación, todos los servicios deshabilitados|\<Falta la clave >|

## <a name="see-also"></a>Vea también

[Habilitar y deshabilitar servicios OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)