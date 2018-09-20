---
title: Fundamentos de WinInet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98ca2eab519cdfa3140d40adfd83070976dcc965
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435654"
---
# <a name="wininet-basics"></a>Fundamentos de WinInet

Puede usar WinInet para agregar compatibilidad con FTP para descargar y cargar archivos desde su aplicación. Puede invalidar [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) y usar el *dwContext* parámetro para proporcionar información de progreso a los usuarios como para busca y descargar archivos.

Este artículo contiene los temas siguientes:

- [Crear un explorador muy Simple](#_core_create_a_very_simple_browser)

- [Descargar una página Web](#_core_download_a_web_page)

- [Un archivo FTP](#_core_ftp_a_file)

- [Recuperar un directorio Gopher](#_core_retrieve_a_gopher_directory)

- [Mostrar información de progreso durante la transferencia de archivos](#_core_display_progress_information_while_transferring_files)

Los fragmentos de código siguientes muestran cómo crear un simple explorador, descargar una página Web, un archivo, FTP y buscar un archivo gopher. No se ha diseñado como ejemplos completos y no incluyen el control de excepciones.

Para obtener más información sobre WinInet, vea [extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md).

##  <a name="_core_create_a_very_simple_browser"></a> Crear un explorador muy Simple

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

##  <a name="_core_download_a_web_page"></a> Descargar una página Web

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

##  <a name="_core_ftp_a_file"></a> Un archivo FTP

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

##  <a name="_core_retrieve_a_gopher_directory"></a> Recuperar un directorio Gopher

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>Utilizar OnStatusCallback

Al usar las clases WinInet, puede usar el [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) miembro de la aplicación [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto para recuperar información de estado. Si deriva sus propias `CInternetSession` de objetos, invalidar `OnStatusCallback`y habilitar las devoluciones de llamada de estado, MFC llamará a su `OnStatusCallback` función con la información de progreso sobre toda la actividad en esa sesión de Internet.

Dado que una sola sesión puede admitir varias conexiones (que, durante su ciclo de vida, pueden realizar muchas operaciones distintas), `OnStatusCallback` necesita un mecanismo para identificar cada cambio de estado con una conexión o transacción determinada. Ese mecanismo es proporcionado por el parámetro de Id. de contexto dado a muchas de las funciones miembro en las clases de soporte técnico de WinInet. Este parámetro siempre es del tipo **DWORD** y siempre se denomina *dwContext*.

El contexto que se asigna a un objeto concreto de Internet sólo se utiliza para identificar la actividad que hace que el objeto en el `OnStatusCallback` miembro de la `CInternetSession` objeto. La llamada a `OnStatusCallback` recibe varios parámetros; estos parámetros funcionan conjuntamente para indicar a la aplicación se ha realizado el progreso de la transacción y la conexión.

Cuando creas un `CInternetSession` objeto, puede especificar un *dwContext* parámetro al constructor. `CInternetSession` Sí no usa el identificador de contexto en su lugar, pasa el identificador de contexto con cualquiera **InternetConnection**-explícitamente no obtención un identificador de contexto de sus propios objetos derivados. A su vez, los `CInternetConnection` objetos pasará el identificador de contexto a `CInternetFile` objetos que crean si no se especifica explícitamente un identificador de contexto diferente. Por otro lado, si especifica un identificador de contexto específico de su propio, el objeto y cualquier trabajo que se asociarán con ese identificador de contexto. Puede usar los identificadores de contexto para identificar qué información de estado se entrega para usted en su `OnStatusCallback` función.

##  <a name="_core_display_progress_information_while_transferring_files"></a> Mostrar información de progreso durante la transferencia de archivos

Por ejemplo, si escribe una aplicación que crea una conexión con un servidor FTP para leer un archivo y también se conecta a un servidor HTTP para obtener una página Web, tendrá un `CInternetSession` (objeto), dos `CInternetConnection` objetos (uno sería un `CFtpSession` y el otro sería un `CHttpSession`) y dos `CInternetFile` objetos (uno para cada conexión). Si usa los valores predeterminados para el *dwContext* parámetros, no sería capaz de distinguir entre el `OnStatusCallback` invocaciones que indican el progreso de la conexión FTP y las invocaciones que indican el progreso de la Conexión de HTTP. Si especifica un *dwContext* identificador, que se puede comprobar más adelante en `OnStatusCallback`, sabrá qué operación generó la devolución de llamada.

## <a name="see-also"></a>Vea también

[Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

