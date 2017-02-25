---
title: "CDaoWorkspaceInfo (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoWorkspaceInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoWorkspaceInfo (estructura)"
  - "DAO (objetos de acceso a datos), colección de áreas de trabajo"
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoWorkspaceInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CDaoWorkspaceInfo` contiene información sobre un área de trabajo definida para el acceso a bases de datos de \(DAO\) de objetos de acceso a datos.  
  
## Sintaxis  
  
```  
  
      struct CDaoWorkspaceInfo  
{  
   CString m_strName;           // Primary  
   CString m_strUserName;       // Secondary  
   BOOL m_bIsolateODBCTrans;    // All  
};  
```  
  
#### Parámetros  
 `m_strName`  
 Nombres de forma única el objeto del área de trabajo.  Para recuperar el valor de esta propiedad directamente, llame a la función miembro de [GetName](../Topic/CDaoQueryDef::GetName.md) del objeto de tabla.  Para obtener más información, vea el tema “propiedad Name” en la Ayuda de DAO.  
  
 *m\_strUserName*  
 Un valor que representa el propietario de un objeto del área de trabajo.  Para obtener información relacionada, vea el tema “propiedad username” en la Ayuda de DAO.  
  
 *m\_bIsolateODBCTrans*  
 Se aísla un valor que indica si las varias transacciones que implican la misma base de datos ODBC.  Para obtener más información, vea [CDaoWorkspace::SetIsolateODBCTrans](../Topic/CDaoWorkspace::SetIsolateODBCTrans.md).  Para obtener información relacionada, vea el tema “propiedades de IsolateODBCTrans” en la Ayuda de DAO.  
  
## Comentarios  
 El área de trabajo es un objeto de clase [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md).  Las referencias a principal, a Secondary, y a Todo anterior indican cómo la información es devuelta por la función miembro de [GetWorkspaceInfo](../Topic/CDaoWorkspace::GetWorkspaceInfo.md) en la clase `CDaoWorkspace`.  
  
 La información recuperada por la función miembro de [CDaoWorkspace::GetWorkspaceInfo](../Topic/CDaoWorkspace::GetWorkspaceInfo.md) se almacena en una estructura de `CDaoWorkspaceInfo` .  `CDaoWorkspaceInfo` también define una función miembro de `Dump` en versiones de depuración.  Puede utilizar `Dump` para volcar el contenido de un objeto de `CDaoWorkspaceInfo` .  
  
## Requisitos  
 **Header:** afxdao.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)