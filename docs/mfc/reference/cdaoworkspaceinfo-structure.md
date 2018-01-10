---
title: CDaoWorkspaceInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoWorkspaceInfo
dev_langs: C++
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e154e2672a9410af979c2e5aa0f6fb0aba7a50f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo (Estructura)
El `CDaoWorkspaceInfo` estructura contiene información sobre un área de trabajo definido para el acceso a la base de datos de datos acceso a objetos (DAO).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CDaoWorkspaceInfo  
{  
    CString m_strName;           // Primary  
    CString m_strUserName;       // Secondary  
    BOOL m_bIsolateODBCTrans;    // All  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 `m_strName`  
 Identifica inequívocamente el objeto de área de trabajo. Para recuperar el valor de esta propiedad directamente, llaman al objeto de definición de consulta [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) función miembro. Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
 *m_strUserName*  
 Un valor que representa el propietario de un objeto de área de trabajo. Para obtener información relacionada, vea el tema "Propiedad de nombre de usuario" en la Ayuda de DAO.  
  
 *m_bIsolateODBCTrans*  
 Un valor que indica si varias transacciones que implican la misma base de datos ODBC están aisladas. Para obtener más información, consulte [CDaoWorkspace:: SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Para obtener información relacionada, vea el tema "IsolateODBCTrans (propiedad)" en la Ayuda de DAO.  
  
## <a name="remarks"></a>Comentarios  
 El área de trabajo es un objeto de clase [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Las referencias a principal, secundaria y todo lo anterior indican cómo se devuelve la información de la [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) función de miembro de clase `CDaoWorkspace`.  
  
 La información recuperada por la [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) función miembro se almacena en un `CDaoWorkspaceInfo` estructura. `CDaoWorkspaceInfo`También define un `Dump` compila la función miembro en versiones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoWorkspaceInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)
