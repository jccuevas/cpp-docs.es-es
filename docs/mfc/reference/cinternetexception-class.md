---
title: Clase de la clase CInternetException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInternetException
dev_langs:
- C++
helpviewer_keywords:
- exception handling, Internet operations
- exceptions, Internet
- CInternetException class
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
caps.latest.revision: 22
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
ms.openlocfilehash: a128095cfc443f0ea8de4cb4028b903929a83f47
ms.lasthandoff: 02/24/2017

---
# <a name="cinternetexception-class"></a>Clase CInternetException (clase)
Representa una condición de excepción relacionada con una operación de Internet.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CInternetException : public CException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInternetException::CInternetException](#cinternetexception)|Construye un objeto `CInternetException`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInternetException::m_dwContext](#m_dwcontext)|El valor de contexto asociado a la operación que provocó la excepción.|  
|[CInternetException::m_dwError](#m_dwerror)|El error que provocó la excepción.|  
  
## <a name="remarks"></a>Comentarios  
 La `CInternetException` clase incluye dos miembros de datos públicos: uno contiene el código de error asociado a la excepción y el otro contiene el identificador de contexto de la aplicación de Internet asociado con el error.  
  
 Para obtener más información acerca de los identificadores de contexto para aplicaciones de Internet, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CInternetException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="a-namecinternetexceptiona--cinternetexceptioncinternetexception"></a><a name="cinternetexception"></a>CInternetException::CInternetException  
 Esta función miembro se llama cuando un `CInternetException` se crea el objeto.  
  
```  
CInternetException(DWORD dwError);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwError`  
 El error que provocó la excepción.  
  
### <a name="remarks"></a>Comentarios  
 Para producir una clase CInternetException, llame a la función global de MFC [AfxThrowInternetException](http://msdn.microsoft.com/library/c9645b10-9541-48b2-8b0c-94ca33fed3cb).  
  
##  <a name="a-namemdwcontexta--cinternetexceptionmdwcontext"></a><a name="m_dwcontext"></a>CInternetException::m_dwContext  
 El valor de contexto asociado con la operación de Internet relacionada.  
  
```  
DWORD_PTR m_dwContext;  
```  
  
### <a name="remarks"></a>Comentarios  
 El identificador de contexto se especificó originalmente en [CInternetSession](../../mfc/reference/cinternetsession-class.md) y pasa a la biblioteca MFC [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- y [CInternetFile](../../mfc/reference/cinternetfile-class.md)-las clases derivadas. Puede invalidar este valor predeterminado y asignar cualquiera `dwContext` parámetro un valor de su elección. `dwContext`se asocia a cualquier operación del objeto especificado. `dwContext`identifica la información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).  
  
##  <a name="a-namemdwerrora--cinternetexceptionmdwerror"></a><a name="m_dwerror"></a>CInternetException::m_dwError  
 El error que provocó la excepción.  
  
```  
DWORD m_dwError;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este valor de error puede ser un sistema de código de error, se encuentra en el archivo WINERROR. H o un valor de error de WININET. H.  
  
 Para obtener una lista de códigos de error de Win32, vea [códigos de Error](http://msdn.microsoft.com/library/windows/desktop/ms681381). Para obtener una lista de mensajes de error de Internet específicos, consulte. Ambos temas están en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [CException (clase)](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CException (clase)](../../mfc/reference/cexception-class.md)

