---
title: CDaoDatabaseInfo (Estructura)
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 46d8056ee4ab478b65f3ef0bd59d88bd3af9b28c
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096158"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo (Estructura)

La `CDaoDatabaseInfo` estructura contiene información sobre un objeto de base de datos definido para los objetos de acceso a datos (DAO).
DAO 3,6 es la versión final y se considera obsoleta.

## <a name="syntax"></a>Sintaxis

```
struct CDaoDatabaseInfo
{
    CString m_strName;       // Primary
    BOOL m_bUpdatable;       // Primary
    BOOL m_bTransactions;    // Primary
    CString m_strVersion;    // Secondary
    long m_lCollatingOrder;  // Secondary
    short m_nQueryTimeout;   // Secondary
    CString m_strConnect;    // All
};
```

#### <a name="parameters"></a>Parámetros

*m_strName*<br/>
Designa de forma única el objeto de base de datos. Para recuperar directamente esta propiedad, llame a [CDaoDatabase:: GetName](../../mfc/reference/cdaodatabase-class.md#getname). Para obtener más información, vea el tema "propiedad Name" en la ayuda de DAO.

*m_bUpdatable*<br/>
Indica si se pueden realizar cambios en la base de datos. Para recuperar directamente esta propiedad, llame a [CDaoDatabase:: CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Para obtener más información, vea el tema "propiedad actualizable" en la ayuda de DAO.

*m_bTransactions*<br/>
Indica si un origen de datos admite transacciones, la grabación de una serie de cambios que se pueden revertir (Cancelar) o confirmar (guardar). Si una base de datos se basa en el motor de base de datos de Microsoft Jet, la propiedad Transactions es distinto de cero y se pueden utilizar transacciones. Es posible que otros motores de base de datos no admitan transacciones. Para recuperar directamente esta propiedad, llame a [CDaoDatabase:: CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Para obtener más información, vea el tema "propiedad Transactions" en la ayuda de DAO.

*m_strVersion*<br/>
Indica la versión del motor de base de datos de Microsoft Jet. Para recuperar el valor de esta propiedad directamente, llame a la función miembro [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) del objeto de base de datos. Para obtener más información, vea el tema "propiedad version" en la ayuda de DAO.

*m_lCollatingOrder*<br/>
Especifica la secuencia del criterio de ordenación en texto para la comparación o ordenación de cadenas. Entre los posibles valores se incluyen:

- `dbSortGeneral`Use el criterio de ordenación general (Inglés, Francés, alemán, Portugués, Italiano y español moderno).

- `dbSortArabic`Use el criterio de ordenación árabe.

- `dbSortCyrillic`Use el criterio de ordenación ruso.

- `dbSortCzech`Use el criterio de ordenación Checo.

- `dbSortDutch`Use el criterio de ordenación holandés.

- `dbSortGreek`Use el criterio de ordenación griego.

- `dbSortHebrew`Use el criterio de ordenación hebreo.

- `dbSortHungarian`Use el criterio de ordenación Húngaro.

- `dbSortIcelandic`Use el criterio de ordenación islandés.

- `dbSortNorwdan`Use el criterio de ordenación noruego o danés.

- `dbSortPDXIntl`Usar el criterio de ordenación internacional de Paradox.

- `dbSortPDXNor`Use el criterio de ordenación noruego o danés de Paradox.

- `dbSortPDXSwe`Use el criterio de ordenación sueco o finlandés de Paradox.

- `dbSortPolish`Use el criterio de ordenación polaco.

- `dbSortSpanish`Use el criterio de ordenación español.

- `dbSortSwedFin`Use el criterio de ordenación sueco o finlandés.

- `dbSortTurkish`Use el criterio de ordenación turco.

- `dbSortUndefined`El criterio de ordenación es undefined o Unknown.

Para obtener más información, vea el tema "personalizar la configuración del registro de Windows para el acceso a datos" en la ayuda de DAO.

*m_nQueryTimeout*<br/>
El número de segundos que el motor de base de datos de Microsoft Jet espera antes de que se produzca un error de tiempo de espera cuando se ejecuta una consulta en una base de datos ODBC. El valor de tiempo de espera predeterminado es de 60 segundos. Cuando QueryTimeout se establece en 0, no se produce ningún tiempo de espera. Esto puede hacer que el programa deje de responder. Para recuperar el valor de esta propiedad directamente, llame a la función miembro [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) del objeto de base de datos. Para obtener más información, vea el tema "propiedad QueryTimeout" en la ayuda de DAO.

*m_strConnect*<br/>
Proporciona información sobre el origen de una base de datos abierta. Para obtener información sobre las cadenas de conexión y para obtener información sobre cómo recuperar el valor de esta propiedad directamente, vea la función miembro [CDaoDatabase:: GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) . Para obtener más información, vea el tema "propiedad de conexión" en la ayuda de DAO.

## <a name="remarks"></a>Comentarios

La base de datos es un objeto DAO que subyace a un objeto MFC de la clase [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Las referencias a principal, secundaria y todas las anteriores indican cómo se devuelve la información mediante la función miembro [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) .

La información recuperada por la función miembro [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) se almacena `CDaoDatabaseInfo` en una estructura. Llame `GetDatabaseInfo` a para `CDaoWorkspace` el objeto en cuya colección de bases de datos se almacena el objeto de base de datos. `CDaoDatabaseInfo`también define una `Dump` función miembro en las compilaciones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoDatabaseInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)
