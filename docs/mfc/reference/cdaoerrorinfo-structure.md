---
title: CDaoErrorInfo (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c11ebaa7d315d09cea40b4ddc94d5afff498bf7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366634"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo (Estructura)
El `CDaoErrorInfo` estructura contiene información acerca de un objeto de error definido para objetos de acceso a datos (DAO).  
  
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
 *m_lErrorCode*  
 Un código de error numérico de DAO. Vea el tema "Errores interceptables de acceso de datos" en la Ayuda de DAO.  
  
 *m_strSource*  
 El nombre del objeto o la aplicación que generó originalmente el error. La propiedad Source especifica una expresión de cadena que representa el objeto que generó originalmente el error; la expresión suele ser el nombre de la clase del objeto. Para obtener más información, vea el tema "Propiedad de origen" en la Ayuda de DAO.  
  
 *m_strDescription*  
 Una cadena descriptiva asociada con un error. Para obtener más información, vea el tema "Descripción de la propiedad" en la Ayuda de DAO.  
  
 *m_strHelpFile*  
 Ruta de acceso completa a un archivo de Ayuda de Microsoft Windows. Para obtener más información, vea el tema "HelpContext, HelpFile propiedades" en la Ayuda de DAO.  
  
 *m_lHelpContext*  
 Un identificador de contexto para un tema en un archivo de Ayuda de Microsoft Windows. Para obtener más información, vea el tema "HelpContext, HelpFile propiedades" en la Ayuda de DAO.  
  
## <a name="remarks"></a>Comentarios  
 MFC no encapsula los objetos de error DAO en una clase. En su lugar, el [CDaoException](../../mfc/reference/cdaoexception-class.md) clase proporciona una interfaz para tener acceso a la colección de errores incluida en DAO **DBEngine** (objeto), el objeto que contiene también todas las áreas de trabajo. Cuando se inicia una operación de DAO de MFC un `CDaoException` del objeto que se detecta, MFC rellena un `CDaoErrorInfo` de la estructura y la almacena en el objeto de excepción [miembro m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) miembro. (Si lo desea llamar a DAO directamente, debe llamar el objeto de excepción [GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) función miembro para rellenar `m_pErrorInfo`.)  
  
 Para obtener más información sobre el control de errores DAO, vea el artículo [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md). Para obtener información relacionada, vea el tema "Error (objeto)" en la Ayuda de DAO.  
  
 La información recuperada por la [CDaoException:: GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) función miembro se almacena en un `CDaoErrorInfo` estructura. Examine la [miembro m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) miembro de datos de un `CDaoException` objeto que se detecta en un controlador de excepciones o llamada `GetErrorInfo` desde un `CDaoException` objeto que se crea explícitamente con el fin de comprobar los errores que puedan tener se produjo durante una llamada directa a las interfaces DAO. `CDaoErrorInfo` También define un `Dump` compila la función miembro en versiones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoErrorInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoException (clase)](../../mfc/reference/cdaoexception-class.md)
