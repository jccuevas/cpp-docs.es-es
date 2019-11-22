---
title: CDaoErrorInfo (Estructura)
ms.date: 09/17/2019
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: 8d731c8e8bea1adc850ab3c00c7688b9f8c9b819
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304233"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo (Estructura)

La estructura `CDaoErrorInfo` contiene información sobre un objeto error definido para los objetos de acceso a datos (DAO). DAO 3,6 es la versión final y se considera obsoleta.

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

MFC no encapsula los objetos de error de DAO en una clase. En su lugar, la clase [CDaoException](../../mfc/reference/cdaoexception-class.md) proporciona una interfaz para tener acceso a la colección de errores incluida en el objeto de `DBEngine` Dao, el objeto que también contiene todas las áreas de trabajo. Cuando una operación DAO de MFC inicia una `CDaoException` objeto que se detecta, MFC rellena una estructura `CDaoErrorInfo` y la almacena en el miembro [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) del objeto de la excepción. (Si decide llamar directamente a DAO, debe llamar a la función miembro [GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) del objeto de la excepción para rellenar `m_pErrorInfo`).

Para obtener más información sobre el control de errores DAO, vea el artículo [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md). Para obtener información relacionada, vea el tema "objeto error" en la ayuda de DAO.

La información recuperada por la función miembro [CDaoException:: GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) se almacena en una estructura de `CDaoErrorInfo`. Examine el [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) miembro de datos de un objeto de `CDaoException` que detecte en un controlador de excepciones, o llame a `GetErrorInfo` desde un objeto de `CDaoException` que cree explícitamente para comprobar los errores que podrían haberse producido durante una llamada directa a las interfaces de DAO. `CDaoErrorInfo` también define una función miembro de `Dump` en las compilaciones de depuración. Puede usar `Dump` para volcar el contenido de un objeto `CDaoErrorInfo`.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoException (clase)](../../mfc/reference/cdaoexception-class.md)
