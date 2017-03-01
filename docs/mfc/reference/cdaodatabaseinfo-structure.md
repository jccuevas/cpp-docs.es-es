---
title: CDaoDatabaseInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoDatabaseInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoDatabaseInfo structure
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ed7eb8612099daf59cb7e722434102095122f3d1
ms.lasthandoff: 02/24/2017

---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo (Estructura)
El `CDaoDatabaseInfo` estructura contiene información sobre un objeto de base de datos definido para los objetos de acceso a datos (DAO).  
  
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
 Nombres de forma exclusiva el objeto de base de datos. Para recuperar directamente esta propiedad, llamada [CDaoDatabase::GetName](../../mfc/reference/cdaodatabase-class.md#getname). Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
 `m_bUpdatable`  
 Indica si se pueden realizar cambios a la base de datos. Para recuperar directamente esta propiedad, llamada [CDaoDatabase::CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Para obtener más información, vea el tema "Propiedad actualizable" en la Ayuda de DAO.  
  
 *m_bTransactions*  
 Indica si un origen de datos admite transacciones, la grabación de una serie de cambios que posteriormente se puede deshacer (cancelar) o confirmada (Guardar). Si una base de datos se basa en el motor de base de datos Microsoft Jet, la propiedad Transactions es distinto de cero y puede utilizar transacciones. Es podrán que otros motores de base de datos no admitan transacciones. Para recuperar directamente esta propiedad, llamada [CDaoDatabase::CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Para obtener más información, vea el tema "Propiedad de transacciones" en la Ayuda de DAO.  
  
 *m_strVersion*  
 Indica la versión del motor de base de datos Microsoft Jet. Para recuperar el valor de esta propiedad directamente, llama al objeto de base de datos [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) función miembro. Para obtener más información, vea el tema "Propiedad de versión" en la Ayuda de DAO.  
  
 `m_lCollatingOrder`  
 Especifica la secuencia del criterio de ordenación en texto para comparación de cadenas o de ordenación. Los posibles valores incluyen:  
  
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
  
- **dbSortPDXNor** usar Paradox Noruego o danés de ordenación.  
  
- **dbSortPDXSwe** usar Paradox sueco o finés de ordenación.  
  
- **dbSortPolish** usar el criterio de ordenación polaco.  
  
- **dbSortSpanish** usar el criterio de ordenación español.  
  
- **dbSortSwedFin** usar el criterio de ordenación sueco o finés.  
  
- **dbSortTurkish** usar el criterio de ordenación turco.  
  
- **dbSortUndefined** el criterio de ordenación es indefinido o desconocido.  
  
 Para obtener más información, vea el tema "Personalización de Windows del registro configuración de acceso a datos" en la Ayuda de DAO.  
  
 *m_nQueryTimeout*  
 El número de segundos que el motor de base de datos Microsoft Jet esperará antes de un error de tiempo de espera se produce cuando se ejecuta una consulta en una base de datos ODBC. El valor de tiempo de espera predeterminado es 60 segundos. Cuando QueryTimeout se establece en 0, se produce ningún tiempo de espera; Esto puede provocar que el programa deje de responder. Para recuperar el valor de esta propiedad directamente, llama al objeto de base de datos [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) función miembro. Para obtener más información, vea el tema "Propiedad QueryTimeout" en la Ayuda de DAO.  
  
 `m_strConnect`  
 Proporciona información sobre el origen de una base de datos abierta. Para obtener información acerca las cadenas de conexión y para obtener información acerca de cómo recuperar el valor de esta propiedad directamente, vea la [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) función miembro. Para obtener más información, vea el tema "Propiedad conectarse" en la Ayuda de DAO.  
  
## <a name="remarks"></a>Comentarios  
 La base de datos es un objeto DAO subyacente de un objeto de clase de MFC [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Las referencias al principal, secundaria y todo lo anterior indican cómo devuelve la información de la [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) función miembro.  
  
 La información recuperada por la [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) función miembro se almacena en un `CDaoDatabaseInfo` estructura. Llame a `GetDatabaseInfo` para el `CDaoWorkspace` en cuya colección de bases de datos se almacena el objeto de base de datos de objeto. `CDaoDatabaseInfo`También define un `Dump` se basa en la función miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de una `CDaoDatabaseInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)

