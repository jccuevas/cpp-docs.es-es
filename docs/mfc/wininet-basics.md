---
title: Fundamentos de WinInet
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: b989e5c3df63ee7b5129d01468a0f869772ed286
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367322"
---
# <a name="wininet-basics"></a>Fundamentos de WinInet

Puede usar WinInet para agregar compatibilidad con FTP para descargar y cargar archivos desde la aplicación. Puede invalidar [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) y usar el parámetro *dwContext* para proporcionar información de progreso a los usuarios a medida que busca y descarga archivos.

Ese artículo contiene los siguientes temas:

- [Crear un navegador muy simple](#_core_create_a_very_simple_browser)

- [Descargar una página web](#_core_download_a_web_page)

- [FTP un archivo](#_core_ftp_a_file)

- [Recuperar un directorio de Gopher](#_core_retrieve_a_gopher_directory)

- [Mostrar información de progreso durante la transferencia de archivos](#_core_display_progress_information_while_transferring_files)

Los siguientes extractos de código muestran cómo crear un navegador simple, descargar una página Web, FTP un archivo y buscar un archivo gopher. No se entienden como ejemplos completos y no todos contienen control de excepciones.

Para obtener información adicional sobre WinInet, consulte Extensiones de [Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md).

## <a name="create-a-very-simple-browser"></a><a name="_core_create_a_very_simple_browser"></a>Crear un navegador muy simple

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

## <a name="download-a-web-page"></a><a name="_core_download_a_web_page"></a>Descargar una página web

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

## <a name="ftp-a-file"></a><a name="_core_ftp_a_file"></a>FTP un archivo

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

## <a name="retrieve-a-gopher-directory"></a><a name="_core_retrieve_a_gopher_directory"></a>Recuperar un directorio de Gopher

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>Usar OnStatusCallback

Al usar las clases WinInet, puede usar el miembro [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) del objeto [CInternetSession](../mfc/reference/cinternetsession-class.md) de la aplicación para recuperar información de estado. Si deriva su `CInternetSession` propio `OnStatusCallback`objeto, invalida y habilita devoluciones de llamada de estado, MFC llamará a la función `OnStatusCallback` con información de progreso sobre toda la actividad en esa sesión de Internet.

Dado que una sola sesión puede admitir varias conexiones (que, a lo largo de su vida útil, pueden realizar muchas operaciones distintas diferentes), `OnStatusCallback` necesita un mecanismo para identificar cada cambio de estado con una conexión o transacción determinada. Ese mecanismo lo proporciona el parámetro de identificador de contexto proporcionado a muchas de las funciones miembro en las clases de soporte de WinInet. Este parámetro siempre es de tipo **DWORD** y siempre se denomina *dwContext*.

El contexto asignado a un objeto de Internet determinado solo `OnStatusCallback` se utiliza `CInternetSession` para identificar la actividad que causa el objeto en el miembro del objeto. La llamada `OnStatusCallback` a recibe varios parámetros; estos parámetros trabajan juntos para indicar a la aplicación qué progreso se ha realizado para qué transacción y conexión.

Al crear `CInternetSession` un objeto, puede especificar un parámetro *dwContext* para el constructor. `CInternetSession`no utiliza el identificador de contexto; en su lugar, pasa el identificador de contexto a cualquier objeto derivado de **InternetConnection**que no obtenga explícitamente un identificador de contexto propio. A su `CInternetConnection` vez, esos objetos `CInternetFile` pasarán el identificador de contexto a los objetos que creen si no especifica explícitamente un identificador de contexto diferente. Si, por otro lado, especifica un identificador de contexto específico propio, el objeto y cualquier trabajo que realice se asociará con ese identificador de contexto. Puede utilizar los datos de contexto para identificar qué información `OnStatusCallback` de estado se le proporciona en la función.

## <a name="display-progress-information-while-transferring-files"></a><a name="_core_display_progress_information_while_transferring_files"></a>Mostrar información de progreso durante la transferencia de archivos

Por ejemplo, si escribe una aplicación que crea una conexión con un servidor FTP para leer un archivo y `CInternetSession` también `CInternetConnection` se conecta a `CFtpSession` un servidor HTTP `CHttpSession`para obtener `CInternetFile` una página Web, tendrá un objeto, dos objetos (uno sería a y el otro sería un ) y dos objetos (uno para cada conexión). Si utiliza valores predeterminados para los parámetros *dwContext,* `OnStatusCallback` no podrá distinguir entre las invocaciones que indican el progreso de la conexión FTP y las invocaciones que indican el progreso de la conexión HTTP. Si especifica un id *dwContext,* que puede `OnStatusCallback`probar más adelante en , sabrá qué operación generó la devolución de llamada.

## <a name="see-also"></a>Consulte también

[Fundamentos de programación de Internet de MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)
