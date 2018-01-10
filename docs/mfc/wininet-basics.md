---
title: Fundamentos de WinInet | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f3c9502c720b0f443ace3cfe637fb4826281ecf4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="wininet-basics"></a>Fundamentos de WinInet
Puede usar WinInet para agregar compatibilidad con el FTP para cargar y descargar archivos desde dentro de la aplicación. Puede invalidar [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) y usar el `dwContext` parámetro para proporcionar información de progreso a los usuarios buscar y descargar archivos.  
  
 Este artículo contiene los temas siguientes:  
  
-   [Crear un explorador muy Simple](#_core_create_a_very_simple_browser)  
  
-   [Descargar una página Web](#_core_download_a_web_page)  
  
-   [Un archivo FTP](#_core_ftp_a_file)  
  
-   [Recuperar un directorio Gopher](#_core_retrieve_a_gopher_directory)  
  
-   [Mostrar información de progreso durante la transferencia de archivos](#_core_display_progress_information_while_transferring_files)  
  
 Los fragmentos de código siguientes muestran cómo crear un explorador sencillo, descargar una página Web, un archivo, FTP y buscar un archivo gopher. No están diseñados como ejemplos completos y no incluyen el control de excepciones.  
  
 Para obtener más información sobre WinInet, vea [extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md).  
  
##  <a name="_core_create_a_very_simple_browser"></a>Crear un explorador muy Simple  
 [!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]  
  
##  <a name="_core_download_a_web_page"></a>Descargar una página Web  
 [!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]  
  
##  <a name="_core_ftp_a_file"></a>Un archivo FTP  
 [!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]  
  
##  <a name="_core_retrieve_a_gopher_directory"></a>Recuperar un directorio Gopher  
 [!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]  
  
## <a name="use-onstatuscallback"></a>Utilizar OnStatusCallback  
 Al usar las clases WinInet, puede usar el [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) miembro de la aplicación [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto que se va a recuperar la información de estado. Si deriva su propio `CInternetSession` de objetos, invalidar `OnStatusCallback`y habilitar las devoluciones de llamada de estado, MFC llamará a su `OnStatusCallback` función con la información de progreso sobre toda la actividad en esa sesión de Internet.  
  
 Dado que una sola sesión puede admitir varias conexiones (que, a través de su duración, pueden realizar muchas operaciones distintas), `OnStatusCallback` necesita un mecanismo para identificar cada cambio de estado con una conexión o transacción determinada. Este mecanismo es proporcionado por el parámetro de Id. de contexto dado a muchas de las funciones de miembro en las clases de soporte técnico de WinInet. Este parámetro siempre es del tipo `DWORD` y siempre se denomina `dwContext`.  
  
 El contexto asignado a un determinado objeto de Internet sólo se utiliza para identificar la actividad hace que el objeto en el `OnStatusCallback` miembro de la `CInternetSession` objeto. La llamada a `OnStatusCallback` recibe varios parámetros; estos parámetros funcionan conjuntamente para indicar que la aplicación se ha realizado el progreso de la transacción y la conexión.  
  
 Cuando se crea un `CInternetSession` objeto, puede especificar un `dwContext` parámetro al constructor. `CInternetSession`Sí no usa el identificador de contexto; en su lugar, pasa el identificador de contexto en cualquier **InternetConnection**-objetos que no obtener explícitamente un identificador de contexto de sus propios derivados. A su vez, los `CInternetConnection` objetos pasará el identificador de contexto junto a `CInternetFile` objetos crean si no se especifica explícitamente un identificador de contexto diferentes. Si, por otro lado, especifique un identificador de contexto específica de su elección, el objeto y cualquier trabajo que se asociará con ese identificador de contexto. Puede usar los identificadores de contexto para identificar qué información de estado es que se le ha proporcionado en su `OnStatusCallback` función.  
  
##  <a name="_core_display_progress_information_while_transferring_files"></a>Mostrar información de progreso durante la transferencia de archivos  
 Por ejemplo, si escribe una aplicación que crea una conexión con un servidor FTP para leer un archivo y también se conecta a un servidor HTTP para obtener una página Web, tendrá un `CInternetSession` (objeto), dos `CInternetConnection` objetos (uno sería un **objeto CFtpSession** y el otro sería un **CHttpSession**) y dos `CInternetFile` objetos (uno para cada conexión). Si usa valores predeterminados para la `dwContext` parámetros, no sería capaz de distinguir entre el `OnStatusCallback` invocaciones que indican el progreso de la conexión FTP y las invocaciones que indican el progreso de la conexión HTTP. Si especifica un `dwContext` identificador, que puede probar más adelante en `OnStatusCallback`, sabrá qué operación generó la devolución de llamada.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos de programación de Internet MFC](../mfc/mfc-internet-programming-basics.md)   
 [Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

