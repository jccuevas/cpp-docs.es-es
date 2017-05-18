---
title: CDaoErrorInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoErrorInfo structure
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 3a3b33f6a7b95edcb2476b03356d32e74d1b8954
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo (Estructura)
El `CDaoErrorInfo` estructura contiene información sobre un objeto de error definido para objetos de acceso a datos (DAO).  
  
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
 El nombre del objeto o aplicación que generó originalmente el error. La propiedad Source especifica una expresión de cadena que representa el objeto que generó originalmente el error; la expresión suele ser el nombre de clase del objeto. Para obtener más información, vea el tema "Propiedad de origen" en la Ayuda de DAO.  
  
 *m_strDescription*  
 Una cadena descriptiva asociada a un error. Para obtener más información, vea el tema "Descripción de la propiedad" en la Ayuda de DAO.  
  
 *m_strHelpFile*  
 Ruta de acceso completa a un archivo de Ayuda de Microsoft Windows. Para obtener más información, vea el tema "HelpContext, HelpFile propiedades" en la Ayuda de DAO.  
  
 *m_lHelpContext*  
 Un identificador de contexto para un tema en un archivo de Ayuda de Microsoft Windows. Para obtener más información, vea el tema "HelpContext, HelpFile propiedades" en la Ayuda de DAO.  
  
## <a name="remarks"></a>Comentarios  
 MFC no encapsula los objetos de error DAO en una clase. En su lugar, el [CDaoException](../../mfc/reference/cdaoexception-class.md) clase proporciona una interfaz para tener acceso a la colección de errores incluida en DAO **DBEngine** (objeto), el objeto que contiene todas las áreas de trabajo. Cuando se inicia una operación de DAO de MFC un `CDaoException` de objetos que detecta, MFC ocupa una `CDaoErrorInfo` estructura y lo almacena en el objeto de excepción [miembro m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) miembro. (Si opta por llamar a DAO directamente, debe llamar el objeto de excepción [GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) función miembro para rellenar `m_pErrorInfo`.)  
  
 Para obtener más información sobre el control de errores DAO, vea el artículo [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md). Para obtener información relacionada, vea el tema "Objeto de Error" en la Ayuda de DAO.  
  
 La información recuperada por la [CDaoException:: GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) función miembro se almacena en un `CDaoErrorInfo` estructura. Examine la [miembro m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) miembro de datos de un `CDaoException` objeto que se detecta un controlador de excepciones o llamar a `GetErrorInfo` de un `CDaoException` que crear explícitamente para comprobar los errores que pudieran haberse producido durante una llamada directa a las interfaces DAO. `CDaoErrorInfo`También define un `Dump` se basa en la función miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de una `CDaoErrorInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Clase CDaoException](../../mfc/reference/cdaoexception-class.md)

