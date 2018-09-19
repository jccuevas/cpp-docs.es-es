---
title: CDaoTableDefInfo (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoTableDefInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac88b3fd55a81237e6c54dbad422f9537950c9e6
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335771"
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo (Estructura)
El `CDaoTableDefInfo` estructura contiene información sobre un objeto de definición de tabla definido para los objetos de acceso a datos (DAO).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CDaoTableDefInfo  
{  
    CString m_strName;               // Primary  
    BOOL m_bUpdatable;               // Primary  
    long m_lAttributes;              // Primary  
    COleDateTime m_dateCreated;      // Secondary  
    COleDateTime m_dateLastUpdated;  // Secondary  
    CString m_strSrcTableName;       // Secondary  
    CString m_strConnect;            // Secondary  
    CString m_strValidationRule;     // All  
    CString m_strValidationText;     // All  
    long m_lRecordCount;             // All  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 *m_strName*  
 Identifica inequívocamente el objeto de definición de tabla. Para recuperar el valor de esta propiedad directamente, llame el objeto de definición de tabla [GetName](../../mfc/reference/cdaotabledef-class.md#getname) función miembro. Para obtener más información, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.  
  
 *m_bUpdatable*  
 Indica si se pueden realizar cambios a la tabla. La forma más rápida para determinar si una tabla es actualizable es abrir un `CDaoTableDef` para la tabla de objetos y llamar al objeto [CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate) función miembro. `CanUpdate` siempre devuelve cero (TRUE) para un objeto de definición de tabla recién creada y 0 (FALSE) para un objeto de definición de tabla adjunta. Solo para una base de datos para el que el usuario actual tiene permiso de escritura se puede anexar un nuevo objeto de definición de tabla. Si la tabla contiene solo campos no actualizable, `CanUpdate` devuelve 0. Cuando uno o más campos son actualizables, `CanUpdate` devuelve cero. Puede editar sólo los campos actualizables. Para obtener más información, vea el tema "Propiedad actualizable" en la Ayuda de DAO.  
  
 *m_lAttributes*  
 Especifica las características de la tabla representada por el objeto de definición de tabla. Para recuperar los atributos de una definición de tabla actuales, llame a su [GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes) función miembro. El valor devuelto puede ser una combinación de estas constantes largas (mediante la operación bit a bit OR (**&#124;**) operador):  
  
- `dbAttachExclusive` Para las bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que la tabla es una tabla asociada abierta para uso exclusivo.  
  
- `dbAttachSavePWD` Para las bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que el Id. de usuario y la contraseña para la tabla asociada se guardan con la información de conexión.  
  
- `dbSystemObject` Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos Microsoft Jet. (Solo lectura).  
  
- `dbHiddenObject` Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos Microsoft Jet (para su uso temporal). (Solo lectura).  
  
- `dbAttachedTable` Indica que la tabla es una tabla de una base de datos que no son ODBC, como una base de datos de Paradox asociada.  
  
- `dbAttachedODBC` Indica que la tabla es una tabla de una base de datos ODBC, como Microsoft SQL Server asociada.  
  
 *m_dateCreated*  
 La fecha y hora de que creación de la tabla. Para recuperar directamente la fecha de creación de la tabla, llame el [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) función miembro de la `CDaoTableDef` objeto asociado a la tabla. Para obtener más información, vea los comentarios a continuación. Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
 *m_dateLastUpdated*  
 La fecha y hora de los cambios más recientes realizados en el diseño de la tabla. Para recuperar directamente la fecha en que se actualizó por última vez la tabla, llame el [GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated) función miembro de la `CDaoTableDef` objeto asociado a la tabla. Para obtener más información, vea los comentarios a continuación. Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
 *m_strSrcTableName*  
 Especifica el nombre de una tabla asociada, si existe. Para recuperar directamente el nombre de la tabla de origen, llame el [GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename) función miembro de la `CDaoTableDef` objeto asociado a la tabla.  
  
 *m_strConnect*  
 Proporciona información sobre el origen de una base de datos abierta. Puede comprobar esta propiedad mediante una llamada a la [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) función miembro de su `CDaoTableDef` objeto. Para obtener más información acerca de las cadenas de conexión, vea `GetConnect`.  
  
 *m_strValidationRule*  
 Un valor que valida los datos de los campos de definición de tabla a medida que se modifiquen o se agregan a una tabla. Validación solo se admite para las bases de datos que utilizan el motor de base de datos Microsoft Jet. Para recuperar directamente la regla de validación, llame el [GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule) función miembro de la `CDaoTableDef` objeto asociado a la tabla. Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.  
  
 *m_strValidationText*  
 Un valor que especifica el texto del mensaje que la aplicación debe mostrar si no se cumple la regla de validación especificada por la propiedad ValidationRule. Para obtener información relacionada, vea el tema "Propiedad de texto de validación" en la Ayuda de DAO.  
  
 *m_lRecordCount*  
 El número de registros que se obtiene acceso en un objeto de definición de tabla. Valor de esta propiedad es de solo lectura. Para recuperar directamente el número de registros, llame el [GetRecordCount](../../mfc/reference/cdaotabledef-class.md#getrecordcount) función miembro de la `CDaoTableDef` objeto. La documentación de `GetRecordCount` describe aún más el número de registros. Tenga en cuenta que recuperar este número puede ser una operación mucho tiempo si la tabla contiene muchos registros.  
  
## <a name="remarks"></a>Comentarios  
 La definición de tabla es un objeto de clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Las referencias a principal, secundaria y todo lo anterior indican cómo devuelve la información de la [GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) función miembro de clase `CDaoDatabase`.  
  
 Información recuperada por el [CDaoDatabase:: GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) función miembro se almacena en un `CDaoTableDefInfo` estructura. Llame a la `GetTableDefInfo` función miembro de la `CDaoDatabase` objeto en cuya colección de definiciones de tabla se almacena el objeto de definición de tabla. `CDaoTableDefInfo` También define un `Dump` se basa en función de miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoTableDefInfo` objeto.  
  
 La configuración de fecha y hora se deriva del equipo en el que se creó o actualizó por última vez la tabla base. En un entorno multiusuario, los usuarios deben obtener estos valores directamente desde el servidor de archivos para evitar las discrepancias en la DateCreated y LastUpdated valores de propiedad.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)
