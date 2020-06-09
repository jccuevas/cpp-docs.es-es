---
title: Cómo simplifica MFC la creación de aplicaciones cliente de Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
ms.openlocfilehash: 71b72a3079cd0d0c87289c1813c09a24d9f75c89
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618559"
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>Cómo simplifica MFC la creación de aplicaciones cliente de Internet

Los Microsoft Foundation Classes encapsulan las funciones de la extensión Internet de Win32 (WinInet) de manera que proporciona un contexto conocido para los programadores de MFC. MFC proporciona tres clases de archivos de Internet ([CInternetFile](reference/cinternetfile-class.md), [CHttpFile](reference/chttpfile-class.md)y [CGopherFile (](reference/cgopherfile-class.md)) derivadas de la clase [CStdioFile](reference/cstdiofile-class.md) . Estas clases no solo facilitan la recuperación y manipulación de los datos de Internet de los programadores que han usado `CStdioFile` para los archivos locales, pero con estas clases puede administrar archivos locales y archivos de Internet de forma coherente y transparente.

Las clases WinInet de MFC proporcionan la misma funcionalidad que `CStdioFile` para los datos transferidos a través de Internet. Estas clases abstraen los protocolos de Internet para HTTP, FTP y Gopher en una interfaz de programación de aplicaciones de alto nivel, lo que proporciona una ruta de acceso rápida y sencilla para hacer que las aplicaciones sean compatibles con Internet. Por ejemplo, la conexión a un servidor FTP todavía requiere varios pasos en un nivel bajo, pero como desarrollador de MFC, solo tiene que realizar una llamada a `CInternetSession::GetFTPConnection` para crear esa conexión.

Además, las clases WinInet de MFC proporcionan las siguientes ventajas:

- E/s almacenada en búfer

- Controladores con seguridad de tipos para los datos

- Parámetros predeterminados para muchas funciones

- Control de excepciones para errores comunes de Internet

- Limpieza automática de identificadores y conexiones abiertos

## <a name="see-also"></a>Consulte también

[Extensiones de Internet Win32 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Cómo simplifica WinInet la creación de aplicaciones cliente de Internet](how-wininet-makes-it-easier-to-create-internet-client-applications.md)
