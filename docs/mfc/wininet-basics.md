---
title: "Fundamentos de WinInet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnStatusCallback (método)"
  - "WinInet (clases), acerca de las clases WinInet"
  - "WinInet (clases), mostrar progreso"
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Fundamentos de WinInet
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar WinInet para agregar compatibilidad de FTP para descargar y cargar los archivos dentro de la aplicación.  Puede reemplazar [OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md) y utilizar el parámetro de `dwContext` para proporcionar información sobre el progreso a los usuarios mientras busca y descarga los archivos.  
  
 Este artículo contiene los siguientes temas:  
  
-   [Cree un explorador de Muy Simple](#_core_create_a_very_simple_browser)  
  
-   [Descargue una página Web](#_core_download_a_web_page)  
  
-   [FTP un archivo](#_core_ftp_a_file)  
  
-   [Recuperar un directorio de Gopher](#_core_retrieve_a_gopher_directory)  
  
-   [Muestra información de progreso mientras transfiere los archivos](#_core_display_progress_information_while_transferring_files)  
  
 Los extractos de código siguientes muestran cómo crear un explorador simple, descargar una página Web, FTP un archivo, y busque un archivo de gopher.  No está pensada como los ejemplos completos y no todos contienen control de excepciones.  
  
 Para obtener más información sobre WinInet, vea [Extensiones de Internet para Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md).  
  
##  <a name="_core_create_a_very_simple_browser"></a> Cree un explorador de Muy Simple  
 [!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/CPP/wininet-basics_1.cpp)]  
  
##  <a name="_core_download_a_web_page"></a> Descargue una página Web  
 [!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/CPP/wininet-basics_2.cpp)]  
  
##  <a name="_core_ftp_a_file"></a> FTP un archivo  
 [!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/CPP/wininet-basics_3.cpp)]  
  
##  <a name="_core_retrieve_a_gopher_directory"></a> Recuperar un directorio de Gopher  
 [!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/CPP/wininet-basics_4.cpp)]  
  
## Utilice OnStatusCallback  
 Al utilizar las clases WinInet, puede utilizar el miembro de [OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md) del objeto de [CInternetSession](../mfc/reference/cinternetsession-class.md) de la aplicación a la información de estado de recuperación.  Si deriva posee el objeto de `CInternetSession` , reemplace `OnStatusCallback`, y habilitar las devoluciones de llamada de estado, MFC llamará a la función de `OnStatusCallback` con la información de progreso sobre toda la actividad en esa sesión de internet.  
  
 Dado que una sola sesión podría admitir varias conexiones \(que, en su período de duración, pueden realizar varias operaciones diferentes\), `OnStatusCallback` necesita un mecanismo identificar cada cambio de estado con una conexión o transacción determinada.  Que el mecanismo proporcionado por el parámetro Id. de contexto determinado a muchas de las funciones miembro de las clases de soporte WinInet.  Este parámetro es siempre de `DWORD` escrito y siempre se denomina `dwContext`.  
  
 El contexto asignado a un objeto determinado de internet se utiliza para identificar sólo la actividad las causas de objeto en el miembro de `OnStatusCallback` del objeto de `CInternetSession` .  La llamada a `OnStatusCallback` recibe varios parámetros; estos parámetros colaboran para indicar a la aplicación se ha creado el progreso que transacción y conexión.  
  
 Cuando se crea un objeto de `CInternetSession` , puede especificar un parámetro de `dwContext` al constructor.  `CInternetSession` propio no utiliza el Id. de contexto; en su lugar, pasa el Id. de contexto en cualquier **InternetConnection**\- objetos derivados que no obtienen un Id. de contexto propios.  A su vez, esos objetos de `CInternetConnection` superan el Id. de contexto adelante a los objetos de `CInternetFile` que crean si no especifica otra identificación de contexto  Si, por otro lado, especifica un Id. de contexto específico de dispone, el objeto y cualquier trabajo que lo haga es asociado a esa identificación de contexto  Puede utilizar los id. de contexto para identificar qué información de estado se da se en función de `OnStatusCallback` .  
  
##  <a name="_core_display_progress_information_while_transferring_files"></a> Muestra información de progreso mientras transfiere los archivos  
 Por ejemplo, si escribe una aplicación que cree una conexión a un servidor FTP para leer un archivo y también se conecte a un servidor HTTP para obtener una página Web, tendrá un objeto de `CInternetSession` , dos objetos de `CInternetConnection` \(uno sería **CFtpSession** y el otro se **CHttpSession**\), y dos objetos de `CInternetFile` \(uno para cada conexión\).  Si utiliza los valores predeterminados para los parámetros de `dwContext` , no puede distinguir entre las invocaciones de `OnStatusCallback` que indican el progreso de la conexión de FTP e invocaciones que indican el progreso para la conexión HTTP.  Si especifica un identificador de `dwContext` , que puede probar más adelante en `OnStatusCallback`, sabrá qué operación generó la devolución de llamada.  
  
## Vea también  
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)   
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)