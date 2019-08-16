---
title: CDaoWorkspaceInfo (Estructura)
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspaceInfo
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
ms.openlocfilehash: afbc73c079a6deec3f3e1b7455f9f2dbface5025
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253640"
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

*m_strName*<br/>
Identifica inequívocamente el objeto de área de trabajo. Para recuperar el valor de esta propiedad directamente, llame el objeto de definición de consulta [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) función miembro. Para obtener más información, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.

*m_strUserName*<br/>
Un valor que representa el propietario de un objeto de área de trabajo. Para obtener información relacionada, vea el tema "Propiedad de nombre de usuario" en la Ayuda de DAO.

*m_bIsolateODBCTrans*<br/>
Un valor que indica si varias transacciones que implican la misma base de datos ODBC están aisladas. Para obtener más información, consulte [CDaoWorkspace:: SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Para obtener información relacionada, vea el tema "IsolateODBCTrans Property" en la Ayuda de DAO.

## <a name="remarks"></a>Comentarios

El área de trabajo es un objeto de clase [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Las referencias a principal, secundaria y todo lo anterior indican cómo devuelve la información de la [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) función miembro de clase `CDaoWorkspace`.

Información recuperada por el [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) función miembro se almacena en un `CDaoWorkspaceInfo` estructura. `CDaoWorkspaceInfo` También define un `Dump` se basa en función de miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoWorkspaceInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)
