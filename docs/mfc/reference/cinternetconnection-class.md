---
title: Clase CInternetConnection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInternetConnection
dev_langs:
- C++
helpviewer_keywords:
- asynchronous connections
- CInternetConnection class
- Internet connections
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7f99562e0c6103fc3f46a7fe28f9d2f2efff0a01
ms.lasthandoff: 02/24/2017

---
# <a name="cinternetconnection-class"></a>CInternetConnection (clase)
Administra la conexión a un servidor de Internet.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CInternetConnection : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInternetConnection::CInternetConnection](#cinternetconnection)|Construye un objeto `CInternetConnection`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInternetConnection::GetContext](#getcontext)|Obtiene el identificador de contexto para este objeto de conexión.|  
|[CInternetConnection::GetServerName](#getservername)|Obtiene el nombre del servidor asociado con la conexión.|  
|[CInternetConnection::GetSession](#getsession)|Obtiene un puntero a la [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto asociado a la conexión.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|Identificador de sesión de Internet.|  
  
## <a name="remarks"></a>Comentarios  
 Es la clase base para clases MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [objeto CHttpConnection](../../mfc/reference/chttpconnection-class.md), y [objeto CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Cada una de estas clases proporciona funcionalidad adicional para comunicarse con el servidor FTP, HTTP o gopher respectivo.  
  
 Para comunicarse directamente con un servidor de Internet, debe tener un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto y un `CInternetConnection` objeto.  
  
 Para obtener más información acerca de cómo el WinInet clases de trabajo, consulte el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetConnection`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="a-namecinternetconnectiona--cinternetconnectioncinternetconnection"></a><a name="cinternetconnection"></a>CInternetConnection::CInternetConnection  
 Esta función miembro se llama cuando un `CInternetConnection` se crea el objeto.  
  
```  
CInternetConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSession`  
 Un puntero a un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto.  
  
 `pstrServer`  
 Puntero a una cadena que contiene el nombre del servidor.  
  
 `nPort`  
 El número que identifica el puerto de Internet para esta conexión.  
  
 `dwContext`  
 El identificador de contexto para la `CInternetConnection` objeto. Consulte **comentarios** para obtener más información acerca de `dwContext`.  
  
### <a name="remarks"></a>Comentarios  
 No llamar nunca a `CInternetConnection` usted mismo; en su lugar, llame a la [CInternetSession](../../mfc/reference/cinternetsession-class.md) función de miembro para el tipo de conexión que desea establecer:  
  
- [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)  
  
- [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)  
  
- [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)  
  
 El valor predeterminado de `dwContext` se envía por MFC para la `CInternetConnection`-objeto derivado de la [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto que creó el **InternetConnection**-objeto derivado. El valor predeterminado se establece en 1; Sin embargo, puede asignar explícitamente un identificador de contexto específico en el [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession) constructor para la conexión. El objeto y cualquier trabajo que se asociarán con ese identificador de contexto. El identificador de contexto se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
##  <a name="a-namegetcontexta--cinternetconnectiongetcontext"></a><a name="getcontext"></a>CInternetConnection::GetContext  
 Llame a esta función miembro para obtener el identificador de contexto para esta sesión.  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de contexto de la aplicación asignada.  
  
### <a name="remarks"></a>Comentarios  
 El identificador de contexto se especificó originalmente en [CInternetSession](../../mfc/reference/cinternetsession-class.md) y se propaga a `CInternetConnection`- y [CInternetFile](../../mfc/reference/cinternetfile-class.md)-clases derivadas, a menos que se especifican de forma diferente en la llamada a una función que abre la conexión. El identificador de contexto asociado a cualquier operación del objeto determinado e identifica información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).  
  
 Para obtener más información acerca de cómo **GetContext** funciona con otras clases WinInet para proporcionar la información de estado de usuario, consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
##  <a name="a-namegetservernamea--cinternetconnectiongetservername"></a><a name="getservername"></a>CInternetConnection::GetServerName  
 Llame a esta función miembro para obtener el nombre del servidor asociado con esta conexión a Internet.  
  
```  
CString GetServerName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre del servidor que funciona con este objeto de conexión.  
  
##  <a name="a-namegetsessiona--cinternetconnectiongetsession"></a><a name="getsession"></a>CInternetConnection::GetSession  
 Llame a esta función miembro para obtener un puntero a la `CInternetSession` objeto que está asociado con esta conexión.  
  
```  
CInternetSession* GetSession() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto asociado a este objeto de conexión de Internet.  
  
##  <a name="a-nameoperatorhinterneta--cinternetconnectionoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetConnection::operator HINTERNET  
 Utilice este operador para obtener el identificador de nivel de API para la sesión actual de Internet.  
  
```  
operator HINTERNET() const;  
```  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




