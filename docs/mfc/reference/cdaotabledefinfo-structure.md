---
title: "CDaoTableDefInfo (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoTableDefInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoTableDefInfo (estructura)"
  - "DAO (objetos de acceso a datos), TableDefs (colección)"
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoTableDefInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CDaoTableDefInfo` contiene información sobre un objeto de definición definido para los objetos \(DAO\) de acceso a datos.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `m_strName`  
 Nombres de forma única el objeto de definición.  Para recuperar el valor de esta propiedad directamente, llame a la función miembro de [GetName](../Topic/CDaoTableDef::GetName.md) del objeto de definición.  Para obtener más información, vea el tema “propiedad Name” en la Ayuda de DAO.  
  
 `m_bUpdatable`  
 Indica si se pueden realizar en la tabla.  La rapidez de determinar si una tabla es actualizable es abrir un objeto de `CDaoTableDef` para la tabla y llamar a la función miembro de [CanUpdate](../Topic/CDaoTableDef::CanUpdate.md) del objeto.  `CanUpdate` siempre devuelve cero \(**VERDADERO**\) para un objeto y un 0 creados recientemente de definición \(**FALSE**\) para un objeto adjunto de definición.  Un nuevo objeto de definición se puede anexar solo una base de datos para la que el usuario actual tiene permiso de escritura.  Si la tabla contiene sólo los campos nonupdatable, `CanUpdate` devuelve 0.  Cuando uno o más campos son actualizables, `CanUpdate` devuelve cero.  Puede editar sólo los campos actualizables.  Para obtener más información, vea el tema “propiedades de Actualizable” en la Ayuda de DAO.  
  
 `m_lAttributes`  
 Especifica las características de la tabla representada por el objeto de definición.  Para recuperar atributos actuales de un definición, llame a su función miembro de [GetAttributes](../Topic/CDaoTableDef::GetAttributes.md) .  El valor devuelto puede ser una combinación de estas constantes largas \(mediante bit a bit\- OR \(  **&#124;**\) operador\):  
  
-   las bases de datos de**dbAttachExclusive**For que utilizan el motor de base de datos Microsoft Jet, indican que la tabla es una tabla asociada abierto para el uso exclusivo.  
  
-   las bases de datos de**dbAttachSavePWD**For que utilizan el motor de base de datos Microsoft Jet, indican que el Id. de usuario y la contraseña de la tabla asociada se guardan con la información de conexión.  
  
-   **dbSystemObject** Indica la tabla es una tabla del sistema proporcionada por el motor de base de datos Microsoft Jet. \(Solo lectura\).  
  
-   **dbHiddenObject** Indica la tabla es una tabla oculta proporcionada por el motor de base de datos Microsoft Jet \(para el uso temporal. \(Solo lectura\).  
  
-   **dbAttachedTable** Indica la tabla es una tabla asociada de una base de datos de que ODBC, como una base de datos de Paradox.  
  
-   **dbAttachedODBC** Indica la tabla es una tabla asociada de una base de datos ODBC, como Microsoft SQL Server.  
  
 `m_dateCreated`  
 Fecha y hora en que la tabla se creó.  Para recuperar directamente la fecha que la tabla se creó, llamar a la función miembro de [GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md) del objeto de `CDaoTableDef` asociado a la tabla.  Vea los comentarios más adelante para obtener más información.  Para obtener información relacionada, vea el tema “DateCreated, propiedades de LastUpdated” en la Ayuda de DAO.  
  
 `m_dateLastUpdated`  
 Fecha y hora del cambio realizado más reciente en el diseño de la tabla.  Para recuperar directamente la fecha que la tabla se actualizó, que llama a por última vez la función miembro de [GetDateLastUpdated](../Topic/CDaoTableDef::GetDateLastUpdated.md) del objeto de `CDaoTableDef` asociado a la tabla.  Vea los comentarios más adelante para obtener más información.  Para obtener información relacionada, vea el tema “DateCreated, propiedades de LastUpdated” en la Ayuda de DAO.  
  
 *m\_strSrcTableName*  
 Especifica el nombre de una tabla asociada si existe.  Para recuperar directamente el nombre de la tabla de origen, llame a la función miembro de [GetSourceTableName](../Topic/CDaoTableDef::GetSourceTableName.md) del objeto de `CDaoTableDef` asociado a la tabla.  
  
 `m_strConnect`  
 Proporciona información sobre el origen de una base de datos abierto.  Puede comprobar esta propiedad llamando a la función miembro de [GetConnect](../Topic/CDaoTableDef::GetConnect.md) del objeto de `CDaoTableDef` .  Para obtener más información sobre cadenas conectarse, vea `GetConnect`.  
  
 `m_strValidationRule`  
 Un valor que valida los datos en campos de definición mientras se cambian o se agregan a una tabla.  Validación solo se admite para las bases de datos que utilizan el motor de base de datos Microsoft Jet.  Para recuperar directamente la regla de validación, llame a la función miembro de [GetValidationRule](../Topic/CDaoTableDef::GetValidationRule.md) del objeto de `CDaoTableDef` asociado a la tabla.  Para obtener información relacionada, vea el tema “propiedades de ValidationRule” en la Ayuda de DAO.  
  
 `m_strValidationText`  
 Un valor que especifica el texto del mensaje que la aplicación debe mostrar si la regla de validación especificada por la propiedad de ValidationRule no se cumple.  Para obtener información relacionada, vea el tema “propiedades de ValidationText” en la Ayuda de DAO.  
  
 *m\_lRecordCount*  
 El número de registros obtenidos en un objeto de definición.  El valor de la propiedad es de solo lectura.  Para recuperar directamente el número de registro, llame a la función miembro de [GetRecordCount](../Topic/CDaoTableDef::GetRecordCount.md) del objeto de `CDaoTableDef` .  La documentación de `GetRecordCount` describe el número de registro detenidamente.  Observe que recupera este número puede ser una operación larga si la tabla contiene muchos registros.  
  
## Comentarios  
 El definición es un objeto de la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md).  Las referencias a principal, a Secondary, y a Todo anterior indican cómo la información es devuelta por la función miembro de [GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md) en la clase `CDaoDatabase`.  
  
 La información recuperada por la función miembro de [CDaoDatabase::GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md) se almacena en una estructura de `CDaoTableDefInfo` .  Llame a la función miembro de `GetTableDefInfo` del objeto de `CDaoDatabase` en cuya colección de TableDefs se almacena el objeto de definición.  `CDaoTableDefInfo` también define una función miembro de `Dump` en versiones de depuración.  Puede utilizar `Dump` para volcar el contenido de un objeto de `CDaoTableDefInfo` .  
  
 Los valores de fecha y hora se derivan del equipo en el que la tabla base se creó o actualizado pasado.  En un entorno multiusuario, los usuarios deben obtener estos valores directamente en el servidor de archivos para evitar discrepancias en los valores de propiedades de DateCreated y de LastUpdated.  
  
## Requisitos  
 **Header:** afxdao.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef::CanUpdate](../Topic/CDaoTableDef::CanUpdate.md)   
 [CDaoTableDef::GetAttributes](../Topic/CDaoTableDef::GetAttributes.md)   
 [CDaoTableDef::GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md)   
 [CDaoTableDef::GetDateLastUpdated](../Topic/CDaoTableDef::GetDateLastUpdated.md)   
 [CDaoTableDef::GetRecordCount](../Topic/CDaoTableDef::GetRecordCount.md)   
 [CDaoTableDef::GetSourceTableName](../Topic/CDaoTableDef::GetSourceTableName.md)   
 [CDaoTableDef::GetValidationRule](../Topic/CDaoTableDef::GetValidationRule.md)   
 [CDaoTableDef::GetValidationText](../Topic/CDaoTableDef::GetValidationText.md)