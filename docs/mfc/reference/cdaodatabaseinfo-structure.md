---
title: CDaoDatabaseInfo (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoDatabaseInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7121915671f6e0ab52ae66c53e5ca31fa1faec1c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352745"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo (Estructura)
El `CDaoDatabaseInfo` estructura contiene información sobre un objeto de base de datos definido para objetos de acceso a datos (DAO).  
  
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
 `m_strName`  
 Identifica inequívocamente el objeto de base de datos. Para recuperar directamente esta propiedad, llame a [CDaoDatabase::GetName](../../mfc/reference/cdaodatabase-class.md#getname). Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
 `m_bUpdatable`  
 Indica si se pueden realizar cambios a la base de datos. Para recuperar directamente esta propiedad, llame a [CDaoDatabase::CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Para obtener más información, vea el tema "Propiedad actualizable" en la Ayuda de DAO.  
  
 *m_bTransactions*  
 Indica si un origen de datos admite transacciones, la grabación de una serie de cambios que más adelante se pueda revertir (cancelar) o confirmada (Guardar). Si una base de datos se basa en el motor de base de datos de Microsoft Jet, la propiedad Transactions es distinto de cero y puede utilizar las transacciones. Es podrán que otros motores de base de datos no admitan transacciones. Para recuperar directamente esta propiedad, llame a [CDaoDatabase::CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Para obtener más información, vea el tema "Propiedad de transacciones" en la Ayuda de DAO.  
  
 *m_strVersion*  
 Indica la versión del motor de base de datos de Microsoft Jet. Para recuperar el valor de esta propiedad directamente, llaman al objeto de base de datos [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) función miembro. Para obtener más información, vea el tema "Propiedad de versión" en la Ayuda de DAO.  
  
 `m_lCollatingOrder`  
 Especifica la secuencia del criterio de ordenación en texto para comparación de cadenas u ordenación. Los posibles valores incluyen:  
  
- **dbSortGeneral** usar el criterio de ordenación General (inglés, francés, alemán, portugués, italiano y español moderno).  
  
- **dbSortArabic** usar el criterio de ordenación árabe.  
  
- **dbSortCyrillic** usar el criterio de ordenación ruso.  
  
- **dbSortCzech** usar el criterio de ordenación checo.  
  
- **dbSortDutch** usar el criterio de ordenación neerlandés.  
  
- **dbSortGreek** usar el criterio de ordenación griego.  
  
- **dbSortHebrew** usar el criterio de ordenación hebreo.  
  
- **dbSortHungarian** usar el criterio de ordenación húngaro.  
  
- **dbSortIcelandic** usar el criterio de ordenación islandés.  
  
- **dbSortNorwdan** usar el criterio de ordenación Noruego o danés.  
  
- **dbSortPDXIntl** usar el criterio de ordenación internacional de Paradox.  
  
- **dbSortPDXNor** usar el criterio de ordenación danés o noruego Paradox.  
  
- **dbSortPDXSwe** usar Paradox sueco o finés criterio de ordenación.  
  
- **dbSortPolish** usar el criterio de ordenación polaco.  
  
- **dbSortSpanish** usar el criterio de ordenación español.  
  
- **dbSortSwedFin** usar el criterio de ordenación sueco o finés.  
  
- **dbSortTurkish** usar el criterio de ordenación turco.  
  
- **dbSortUndefined** el criterio de ordenación es indefinido o desconocido.  
  
 Para obtener más información, vea el tema "Personalización de Windows del registro configuración de acceso a datos" en la Ayuda de DAO.  
  
 *m_nQueryTimeout*  
 El número de segundos que espera a que el motor de base de datos de Microsoft Jet antes de un error de tiempo de espera se produce cuando se ejecuta una consulta en una base de datos ODBC. El valor de tiempo de espera predeterminado es 60 segundos. Cuando QueryTimeout se establece en 0, se produce sin tiempo de espera; Esto puede provocar que el programa deje de responder. Para recuperar el valor de esta propiedad directamente, llaman al objeto de base de datos [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) función miembro. Para obtener más información, vea el tema "Propiedad QueryTimeout" en la Ayuda de DAO.  
  
 `m_strConnect`  
 Proporciona información sobre el origen de una base de datos abierta. Para obtener información acerca las cadenas de conexión y para obtener información acerca de cómo recuperar el valor de esta propiedad directamente, vea la [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) función miembro. Para obtener más información, vea el tema "Conectarse Property" en la Ayuda de DAO.  
  
## <a name="remarks"></a>Comentarios  
 La base de datos es un objeto DAO subyacente al objeto de clase MFC [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Las referencias a principal, secundaria y todo lo anterior indican cómo se devuelve la información de la [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) función miembro.  
  
 La información recuperada por la [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) función miembro se almacena en un `CDaoDatabaseInfo` estructura. Llame a `GetDatabaseInfo` para el `CDaoWorkspace` en cuya colección de bases de datos se almacena el objeto de base de datos de objeto. `CDaoDatabaseInfo` También define un `Dump` compila la función miembro en versiones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoDatabaseInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)
