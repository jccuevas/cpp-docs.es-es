---
title: CDaoWorkspaceInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoWorkspaceInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoWorkspaceInfo structure
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
caps.latest.revision: 13
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
ms.openlocfilehash: 44c1ce365a1eecdb2a500998c082c6a9245dffb2
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo (Estructura)
El `CDaoWorkspaceInfo` estructura contiene información sobre un área de trabajo definido para el acceso a la base de datos de datos access objects (DAO).  
  
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
 Nombres de forma exclusiva el objeto de área de trabajo. Para recuperar el valor de esta propiedad directamente, llame el objeto querydef [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) función miembro. Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
 *m_strUserName*  
 Un valor que representa el propietario de un objeto de área de trabajo. Para obtener información relacionada, vea el tema "Propiedad de nombre de usuario" en la Ayuda de DAO.  
  
 *m_bIsolateODBCTrans*  
 Un valor que indica si varias transacciones que implican la misma base de datos ODBC están aisladas. Para obtener más información, consulte [CDaoWorkspace:: SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Para obtener información relacionada, vea el tema "Propiedad IsolateODBCTrans" en la Ayuda de DAO.  
  
## <a name="remarks"></a>Comentarios  
 El área de trabajo es un objeto de clase [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Las referencias al principal, secundaria y todo lo anterior indican cómo devuelve la información de la [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) una función miembro de clase `CDaoWorkspace`.  
  
 La información recuperada por la [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) función miembro se almacena en un `CDaoWorkspaceInfo` estructura. `CDaoWorkspaceInfo`También define un `Dump` se basa en la función miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de una `CDaoWorkspaceInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)

