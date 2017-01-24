---
title: "CDaoErrorInfo (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoErrorInfo (estructura)"
  - "DAO (objetos de acceso a datos), colección de errores"
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoErrorInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CDaoErrorInfo` contiene información sobre un objeto error definido para los objetos \(DAO\) de acceso a datos.  
  
## Sintaxis  
  
```  
  
      struct CDaoErrorInfo  
{  
   long m_lErrorCode;  
   CString m_strSource;  
   CString m_strDescription;  
   CString m_strHelpFile;  
   long m_lHelpContext;  
};  
```  
  
#### Parámetros  
 *m\_lErrorCode*  
 Un código de error numérico de DAO.  Vea el tema “errores de Trappable” en la Ayuda de DAO.  
  
 *m\_strSource*  
 El nombre del objeto o la aplicación que generó originalmente el error.  La propiedad Source especifica una expresión de cadena que representa el objeto que generó originalmente el error; la expresión es normalmente el nombre de clase del objeto.  Para obtener información detallada, vea el tema “propiedad Source” en la Ayuda de DAO.  
  
 *m\_strDescription*  
 Una cadena descriptiva asociada a un error.  Para obtener información detallada, vea el tema “propiedad description” en la Ayuda de DAO.  
  
 *m\_strHelpFile*  
 Una ruta de acceso completa a un archivo de Ayuda de Microsoft Windows.  Para obtener información detallada, vea el tema “HelpContext, propiedades de HelpFile” en la Ayuda de DAO.  
  
 *m\_lHelpContext*  
 Un Id. de contexto para un tema en un archivo de Ayuda de Microsoft Windows.  Para obtener información detallada, vea el tema “HelpContext, propiedades de HelpFile” en la Ayuda de DAO.  
  
## Comentarios  
 MFC no encapsula objetos de error de DAO en una clase.  En su lugar, las fuentes de la clase de [CDaoException](../../mfc/reference/cdaoexception-class.md) una interfaz para tener acceso a la colección de errores contenida en el objeto de DAO **DBEngine** , el objeto que también contiene todas las áreas de trabajo.  Cuando una operación DAO de MFC produce un objeto de `CDaoException` que se detecte, MFC rellena una estructura de `CDaoErrorInfo` y la almacena en el miembro de [m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) del objeto de excepción. \(Si decide llamar directamente a objetos DAO directamente, se debe llamar a la función miembro de [GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md) del objeto de excepción a para rellenar `m_pErrorInfo`.\)  
  
 Para obtener más información sobre cómo administrar los errores de DAO, vea el artículo [Excepciones: Excepciones de base de datos](../../mfc/exceptions-database-exceptions.md).  Para obtener información relacionada, vea el tema “objeto error” en la Ayuda de DAO.  
  
 La información recuperada por la función miembro de [CDaoException::GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md) se almacena en una estructura de `CDaoErrorInfo` .  Examine el miembro de datos de [m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) de un objeto de `CDaoException` que se selecciona en un controlador de excepciones, o llame a `GetErrorInfo` de un objeto de `CDaoException` crear explícitamente para comprobar los errores que pueden haber producido durante una llamada directa a las interfaces de DAO.  `CDaoErrorInfo` también define una función miembro de `Dump` en versiones de depuración.  Puede utilizar `Dump` para volcar el contenido de un objeto de `CDaoErrorInfo` .  
  
## Requisitos  
 **Header:** afxdao.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)