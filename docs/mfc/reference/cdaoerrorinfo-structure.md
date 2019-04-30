---
title: CDaoErrorInfo (Estructura)
ms.date: 11/04/2016
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: dd9610fce88c18ac42de81ed712492766ee705de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399855"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo (Estructura)

El `CDaoErrorInfo` estructura contiene información sobre un objeto de error que se define para los objetos de acceso a datos (DAO).

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
Un código de error numérico de DAO. Vea el tema "Errores interceptables de acceso de datos" en la Ayuda de DAO.

*m_strSource*<br/>
El nombre del objeto o la aplicación que generó originalmente el error. La propiedad Source especifica una expresión de cadena que representa el objeto que generó originalmente el error; la expresión suele ser el nombre de la clase del objeto. Para obtener más información, vea el tema "Propiedad de origen" en la Ayuda de DAO.

*m_strDescription*<br/>
Una cadena descriptiva asociada a un error. Para obtener más información, vea el tema "Descripción de propiedad" en la Ayuda de DAO.

*m_strHelpFile*<br/>
Una ruta de acceso completa a un archivo de Ayuda de Microsoft Windows. Para obtener más información, vea el tema "HelpContext, HelpFile propiedades" en la Ayuda de DAO.

*m_lHelpContext*<br/>
Un identificador de contexto para un tema en un archivo de Ayuda de Microsoft Windows. Para obtener más información, vea el tema "HelpContext, HelpFile propiedades" en la Ayuda de DAO.

## <a name="remarks"></a>Comentarios

MFC no encapsula los objetos de error DAO en una clase. En su lugar, el [CDaoException](../../mfc/reference/cdaoexception-class.md) clase proporciona una interfaz para tener acceso a la colección de errores contenida en DAO `DBEngine` (objeto), el objeto que contiene también todas las áreas de trabajo. Cuando se inicia una operación de DAO de MFC un `CDaoException` de objeto que detecte, MFC rellena un `CDaoErrorInfo` estructurar y lo almacena en el objeto de excepción [miembro m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) miembro. (Si elige llamar a DAO directamente, debe llamar al objeto de excepción [GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) función miembro para rellenar `m_pErrorInfo`.)

Para obtener más información sobre el control de errores DAO, vea el artículo [excepciones: Excepciones de base de datos](../../mfc/exceptions-database-exceptions.md). Para obtener información relacionada, vea el tema "Objeto de Error" en la Ayuda de DAO.

Información recuperada por el [CDaoException:: GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) función miembro se almacena en un `CDaoErrorInfo` estructura. Examine el [miembro m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) miembro de datos de un `CDaoException` objetos que detecta en un controlador de excepciones o llamada `GetErrorInfo` desde un `CDaoException` objeto que cree explícitamente con el fin de comprobar los errores que podrían tener se produjo durante una llamada directa a las interfaces DAO. `CDaoErrorInfo` También define un `Dump` se basa en función de miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoErrorInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoException (clase)](../../mfc/reference/cdaoexception-class.md)
