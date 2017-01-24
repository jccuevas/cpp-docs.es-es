---
title: "CInternetSession Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CInternetSession"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInternetSession class"
  - "Internet sessions"
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
caps.latest.revision: 25
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInternetSession Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea e inicializa sesiones únicas o varias simultáneas de internet y, si es necesario, describe la conexión a un servidor proxy.  
  
## Sintaxis  
  
```  
class CInternetSession : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetSession::CInternetSession](../Topic/CInternetSession::CInternetSession.md)|Crea un objeto `CInternetSession`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetSession::Close](../Topic/CInternetSession::Close.md)|Cierra la conexión a Internet cuando finalizan a la sesión de internet.|  
|[CInternetSession::EnableStatusCallback](../Topic/CInternetSession::EnableStatusCallback.md)|Establece una rutina de devolución de llamada de estado.|  
|[CInternetSession::GetContext](../Topic/CInternetSession::GetContext.md)|Cierra la conexión a Internet cuando finalizan a la sesión de internet.|  
|[CInternetSession::GetCookie](../Topic/CInternetSession::GetCookie.md)|devuelve las cookies para la dirección URL especificada y todas sus direcciones URL primarias.|  
|[CInternetSession::GetCookieLength](../Topic/CInternetSession::GetCookieLength.md)|Recupera la variable que especifica la duración de la cookie almacenada en el búfer.|  
|[CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)|Abra una sesión FTP con un servidor.  Abra una sesión para el usuario.|  
|[CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md)|Abra un servidor gopher para una aplicación que intenta abrir una conexión.|  
|[CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md)|Abra un servidor HTTP para una aplicación que intenta abrir una conexión.|  
|[CInternetSession::OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md)|Actualiza el estado de una operación cuando se habilita la devolución de estado.|  
|[CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md)|Los análisis y abra una dirección URL.|  
|[CInternetSession::SetCookie](../Topic/CInternetSession::SetCookie.md)|establece una cookie para la dirección URL especificada.|  
|[CInternetSession::SetOption](../Topic/CInternetSession::SetOption.md)|Establece opciones para la sesión de internet.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetSession::operator HINTERNET](../Topic/CInternetSession::operator%20HINTERNET.md)|Un identificador de la sesión actual de internet.|  
  
## Comentarios  
 Si la conexión a Internet debe mantenerse para la duración de una aplicación, puede crear un miembro de `CInternetSession` de la clase [CWinApp](../../mfc/reference/cwinapp-class.md).  
  
 Una vez establecida una sesión de internet, puede llamar a [OpenURL](../Topic/CInternetSession::OpenURL.md).  `CInternetSession` a analizar la dirección URL para usted llamando a la función global [AfxParseURL](../Topic/AfxParseURL.md).  Sin tener en cuenta el tipo de protocolo, `CInternetSession` interpreta la dirección URL y la administra.  Puede controlar las solicitudes de los archivos locales identificados con el recurso “file:\/\/” de la dirección URL.  `OpenURL` devolverá un puntero a un objeto de [CStdioFile](../../mfc/reference/cstdiofile-class.md) si el nombre que se pasa es un archivo local.  
  
 Si abre una dirección URL en un servidor de Internet mediante `OpenURL`, puede leer la información del sitio.  Si desea realizar \(por ejemplo, HTTP, FTP, o gopher\) acciones servicio\-específicos en los archivos ubicados en un servidor, debe establecer la conexión correspondiente a ese servidor.  Para abrir una clase determinada de conexión directamente a un servicio determinado, utilice una de las siguientes funciones miembro:  
  
-   [GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md) a abrir una conexión a un servicio de gopher.  
  
-   [GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md) a abrir una conexión a un servicio HTTP.  
  
-   [GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md) a abrir una conexión a un servicio FTP.  
  
 [SetOption](../Topic/CInternetSession::SetOption.md) permite establecer las opciones de consulta de sesión, como valores de tiempo de espera, número de intentos, etc.  
  
 las funciones [SetCookie](../Topic/CInternetSession::SetCookie.md), [GetCookie](../Topic/CInternetSession::GetCookie.md), y [GetCookieLength](../Topic/CInternetSession::GetCookieLength.md) miembro de`CInternetSession` proporcionan un medio para administrar una base de datos de la cookie de Win32, a través de la cual los servidores y scripts conservan la información de estado de la estación de trabajo cliente.  
  
 Para obtener más información sobre las tareas de programación básicas de internet, vea el artículo [Primeros pasos de internet: WinInet](../../mfc/wininet-basics.md).  Para obtener información general sobre cómo utilizar las clases WinInet de MFC, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
> [!NOTE]
>  `CInternetSession` producirá [AfxThrowNotSupportedException](../Topic/AfxThrowNotSupportedException.md) para los tipos de servicio no compatible.  Solo se admiten los tipos de servicio siguientes actualmente: FTP, HTTP, gopher, y archivo.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetSession`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpConnection Class](../../mfc/reference/chttpconnection-class.md)   
 [CFtpConnection Class](../../mfc/reference/cftpconnection-class.md)   
 [CGopherConnection Class](../../mfc/reference/cgopherconnection-class.md)