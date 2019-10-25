---
title: CDaoErrorInfo (Estructura)
ms.date: 09/17/2019
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: a7b273bd2aa6b428bf795c1842455b8bfe187cc8
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096148"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo (Estructura)

La `CDaoErrorInfo` estructura contiene información sobre un objeto de error definido para los objetos de acceso a datos (DAO).
DAO 3,6 es la versión final y se considera obsoleta.


## <a name="syntax"></a>Sintaxis

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

#### <a name="parameters"></a>Parámetros

*m_lErrorCode*<br/>
Código de error de DAO numérico. Vea el tema "errores de acceso a datos recapturables" en la ayuda de DAO.

*m_strSource*<br/>
Nombre del objeto o de la aplicación que generó originalmente el error. La propiedad Source especifica una expresión de cadena que representa el objeto que generó originalmente el error; la expresión suele ser el nombre de clase del objeto. Para obtener más información, vea el tema "propiedad de origen" en la ayuda de DAO.

*m_strDescription*<br/>
Cadena descriptiva asociada a un error. Para obtener más información, vea el tema "propiedad Description" en la ayuda de DAO.

*m_strHelpFile*<br/>
Ruta de acceso completa a un archivo de ayuda de Microsoft Windows. Para obtener más información, vea el tema "HelpContext, propiedades de HelpFile" en la ayuda de DAO.

*m_lHelpContext*<br/>
IDENTIFICADOR de contexto de un tema en un archivo de ayuda de Microsoft Windows. Para obtener más información, vea el tema "HelpContext, propiedades de HelpFile" en la ayuda de DAO.

## <a name="remarks"></a>Comentarios

MFC no encapsula los objetos de error de DAO en una clase. En su lugar, la clase [CDaoException](../../mfc/reference/cdaoexception-class.md) proporciona una interfaz para tener acceso a la colección de errores incluida `DBEngine` en el objeto DAO, el objeto que también contiene todas las áreas de trabajo. Cuando una operación DAO de MFC produce un `CDaoException` objeto que se detecta, MFC rellena una `CDaoErrorInfo` estructura y la almacena en el miembro [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) del objeto de la excepción. (Si decide llamar directamente a DAO, debe llamar a la función miembro [GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) del objeto de la excepción para rellenarla `m_pErrorInfo`).

Para obtener más información sobre el control de errores Dao, [vea el artículo excepciones: Excepciones](../../mfc/exceptions-database-exceptions.md)de base de datos. Para obtener información relacionada, vea el tema "objeto error" en la ayuda de DAO.

La información recuperada por la función miembro [CDaoException:: GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) se almacena `CDaoErrorInfo` en una estructura. Examinar el miembro de datos [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) desde `CDaoException` un objeto que se detecta en un controlador de excepciones o `GetErrorInfo` llamar desde `CDaoException` un objeto creado explícitamente para comprobar los errores que podrían haberse producido durante una llamada directa a las interfaces de DAO. `CDaoErrorInfo`también define una `Dump` función miembro en las compilaciones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoErrorInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoException (clase)](../../mfc/reference/cdaoexception-class.md)
