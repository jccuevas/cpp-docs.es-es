---
title: Reemplazar los valores predeterminados de servicio de un proveedor
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: 4cf3ad1064627f64315822a5045642aa50330d10
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209818"
---
# <a name="overriding-provider-service-defaults"></a>Reemplazar los valores predeterminados de servicio de un proveedor

El valor del registro del proveedor para OLEDB_SERVICES se devuelve como el valor predeterminado de la propiedad de inicialización de [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898(v=vs.85)) en el objeto de origen de datos.

Siempre que exista la entrada del registro, se agregan los objetos del proveedor. El usuario puede invalidar la configuración predeterminada del proveedor para los servicios habilitados estableciendo la propiedad DBPROP_INIT_OLEDBSERVICES antes de la inicialización. Para habilitar o deshabilitar un servicio determinado, el usuario obtiene el valor actual de la propiedad DBPROP_INIT_OLEDBSERVICES, establece o borra el bit de la propiedad determinada que se va a habilitar o deshabilitar, y restablece la propiedad. DBPROP_INIT_OLEDBSERVICES puede establecerse directamente en OLE DB o en la cadena de conexión que se pasa a ADO o `IDataInitialize::GetDatasource`. En la tabla siguiente se enumeran los valores correspondientes para habilitar o deshabilitar servicios individuales.

|Servicios predeterminados habilitados|DBPROP_INIT_OLEDBSERVICES valor de propiedad|Valor en la cadena de conexión|
|------------------------------|------------------------------------------------|--------------------------------|
|Todos los servicios (valor predeterminado)|DBPROPVAL_OS_ENABLEALL|"Servicios de OLE DB =-1;"|
|Todo excepto agrupación y inscripción|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"Servicios de OLE DB =-4;"|
|Todo excepto el cursor del cliente|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Servicios de OLE DB =-5;"|
|Todo excepto agrupación, inscripción y cursor del cliente|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Servicios de OLE DB =-7;"|
|Sin servicios|`~DBPROPVAL_OS_ENABLEALL`|"OLE DB Services = 0;"|

Si no existe la entrada del registro para el proveedor, los administradores de componentes no recopilarán los objetos del proveedor. No se activará ningún servicio, aunque el usuario lo solicite explícitamente.

## <a name="see-also"></a>Consulte también

[Agrupación de recursos](/previous-versions/windows/desktop/ms713655(v=vs.85))<br/>
[Cómo los consumidores usan la agrupación de recursos](/previous-versions/windows/desktop/ms715907(v=vs.85))<br/>
[Cómo funcionan eficazmente los proveedores con la agrupación de recursos](/previous-versions/windows/desktop/ms714906(v=vs.85))<br/>
[Habilitar y deshabilitar servicios OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>
