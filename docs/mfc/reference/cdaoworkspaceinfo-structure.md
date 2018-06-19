---
title: CDaoWorkspaceInfo (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoWorkspaceInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd6979124916e8a9cc1dc723008491bababc0322
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366296"
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
  
 La información recuperada por la [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) función miembro se almacena en un `CDaoWorkspaceInfo` estructura. `CDaoWorkspaceInfo` También define un `Dump` compila la función miembro en versiones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoWorkspaceInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)
