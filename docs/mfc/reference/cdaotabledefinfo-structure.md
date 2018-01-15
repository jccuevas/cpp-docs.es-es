---
title: CDaoTableDefInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoTableDefInfo
dev_langs: C++
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e949cb0348cb55fcee5a940b5753a5a8197e600b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo (Estructura)
El `CDaoTableDefInfo` estructura contiene información sobre un objeto de definición de tabla definido para objetos de acceso a datos (DAO).  
  
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
 `m_strName`  
 Identifica inequívocamente el objeto de definición de tabla. Para recuperar el valor de esta propiedad directamente, llaman al objeto de definición de tabla [GetName](../../mfc/reference/cdaotabledef-class.md#getname) función miembro. Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
 `m_bUpdatable`  
 Indica si se pueden realizar cambios a la tabla. La forma más rápida para determinar si una tabla es actualizable es abrir un `CDaoTableDef` para la tabla de objetos y llamar al objeto [CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate) función miembro. `CanUpdate`siempre devuelve es distinto de cero (**TRUE**) para un objeto de definición de tabla recién creada y 0 (**FALSE**) de un objeto tabledef adjunto. Un nuevo objeto de definición de tabla se puede anexar únicamente a una base de datos para el que el usuario actual tiene permiso de escritura. Si la tabla contiene solo los campos no actualizable, `CanUpdate` devuelve 0. Cuando uno o más campos son actualizables, `CanUpdate` devuelve es distinto de cero. Puede editar sólo los campos actualizables. Para obtener más información, vea el tema "Propiedad actualizable" en la Ayuda de DAO.  
  
 `m_lAttributes`  
 Especifica las características de la tabla representada por el objeto de definición de tabla. Para recuperar los atributos actuales de una definición de tabla, llame a su [GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes) función miembro. El valor devuelto puede ser una combinación de estas constantes largo (mediante la operación bit a bit OR (**&#124;**) operador):  
  
- **dbAttachExclusive** bases de datos que utilizan el motor de base de datos de Microsoft Jet, indica la tabla es una tabla asociada abierta para su uso exclusivo.  
  
- **dbAttachSavePWD** bases de datos que utilizan el motor de base de datos de Microsoft Jet, indica que el Id. de usuario y la contraseña para la tabla asociada se guardan con la información de conexión.  
  
- **dbSystemObject** indica la tabla es una tabla del sistema proporcionada por el motor de base de datos de Microsoft Jet. (Solo lectura).  
  
- **dbHiddenObject** indica la tabla es una tabla oculta proporcionada por el motor de base de datos de Microsoft Jet (para su uso temporal). (Solo lectura).  
  
- **dbAttachedTable** indica la tabla es una tabla asociada desde una base de datos no son ODBC, como una base de datos de Paradox.  
  
- **dbAttachedODBC** indica la tabla es una tabla asociada desde una base de datos ODBC, como Microsoft SQL Server.  
  
 `m_dateCreated`  
 La fecha y hora de que creación de la tabla. Para recuperar directamente la fecha de creación de la tabla, llame a la [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) función miembro de la `CDaoTableDef` objeto asociado a la tabla. Para obtener más información, vea comentarios a continuación. Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
 `m_dateLastUpdated`  
 La fecha y hora del cambio más reciente realizado en el diseño de la tabla. Para recuperar directamente la fecha en que se actualizó por última vez la tabla, llame a la [GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated) función miembro de la `CDaoTableDef` objeto asociado a la tabla. Para obtener más información, vea comentarios a continuación. Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
 *m_strSrcTableName*  
 Especifica el nombre de una tabla asociada, si existe. Para recuperar directamente el nombre de la tabla de origen, llame a la [GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename) función miembro de la `CDaoTableDef` objeto asociado a la tabla.  
  
 `m_strConnect`  
 Proporciona información sobre el origen de una base de datos abierta. Puede comprobar esta propiedad mediante una llamada a la [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) función miembro de su `CDaoTableDef` objeto. Para obtener más información acerca de las cadenas de conexión, consulte `GetConnect`.  
  
 `m_strValidationRule`  
 Un valor que valida los datos de los campos de definición de tabla cuando se modifiquen o se agregan a una tabla. Validación solo se admite para las bases de datos que utilizan el motor de base de datos de Microsoft Jet. Para recuperar directamente la regla de validación, llame a la [GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule) función miembro de la `CDaoTableDef` objeto asociado a la tabla. Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.  
  
 `m_strValidationText`  
 Un valor que especifica el texto del mensaje que la aplicación debe mostrar si no se cumple la regla de validación especificada por la propiedad ValidationRule. Para obtener información relacionada, vea el tema "Propiedad texto de validación" en la Ayuda de DAO.  
  
 *m_lRecordCount*  
 El número de registros que se obtiene acceso en un objeto de definición de tabla. Valor de esta propiedad es de solo lectura. Para recuperar directamente el número de registros, llame a la [GetRecordCount](../../mfc/reference/cdaotabledef-class.md#getrecordcount) función miembro de la `CDaoTableDef` objeto. La documentación de `GetRecordCount` describe aún más el número de registros. Tenga en cuenta que recuperar este número puede ser una operación que consume mucho tiempo si la tabla contiene muchos registros.  
  
## <a name="remarks"></a>Comentarios  
 La definición de tabla es un objeto de clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Las referencias a principal, secundaria y todo lo anterior indican cómo se devuelve la información de la [GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) función de miembro de clase `CDaoDatabase`.  
  
 La información recuperada por la [CDaoDatabase:: GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) función miembro se almacena en un `CDaoTableDefInfo` estructura. Llame a la `GetTableDefInfo` función miembro de la `CDaoDatabase` objeto en cuya colección de definiciones de tabla se almacena el objeto de definición de tabla. `CDaoTableDefInfo`También define un `Dump` compila la función miembro en versiones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoTableDefInfo` objeto.  
  
 La configuración de fecha y hora se deriva del equipo en el que se creó o actualizó por última vez la tabla base. En un entorno multiusuario, los usuarios deben obtener estos valores directamente desde el servidor de archivos para evitar discrepancias en la DateCreated y LastUpdated valores de las propiedades.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Clase CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)
