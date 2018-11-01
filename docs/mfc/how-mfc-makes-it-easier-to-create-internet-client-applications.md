---
title: Cómo simplifica MFC la creación de aplicaciones cliente de Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
ms.openlocfilehash: b288db54a020b0074766ee69debdb9f397d3bd03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573453"
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>Cómo simplifica MFC la creación de aplicaciones cliente de Internet

Microsoft Foundation Classes encapsular las funciones de extensión de Internet Win32 (WinInet) de forma que proporciona un contexto familiar para los programadores MFC. MFC proporciona tres clases de archivos de Internet ([CInternetFile](../mfc/reference/cinternetfile-class.md), [CHttpFile](../mfc/reference/chttpfile-class.md), y [CGopherFile](../mfc/reference/cgopherfile-class.md)) deriva el [CStdioFile](../mfc/reference/cstdiofile-class.md) clase . No solo estas clases Asegúrese de recuperar y manipular datos de Internet familiares para los programadores que hayan usado `CStdioFile` para archivos locales, pero con estas clases pueden controlar archivos locales y los archivos de Internet de forma transparente.

Las clases WinInet de MFC proporcionan la misma funcionalidad que `CStdioFile` para datos que se transfieren a través de Internet. Estas clases abstraen los protocolos de Internet para HTTP, FTP y gopher en una aplicación de alto nivel interfaz de programación, lo que proporciona una ruta de acceso rápido y sencillo para que las aplicaciones basadas en Internet. Por ejemplo, todavía se conecta a un servidor FTP requiere varios pasos en un nivel bajo, pero como programador de MFC, solo necesita realizar una llamada a `CInternetSession::GetFTPConnection` para crear la conexión.

Además, las clases WinInet de MFC proporcionan las siguientes ventajas:

- Almacenado en búfer de E/S

- Identificadores de seguridad de tipos para los datos

- Parámetros predeterminados para muchas funciones

- Control de excepciones para errores comunes de Internet

- Limpieza automática de identificadores abiertos y las conexiones

## <a name="see-also"></a>Vea también

[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Cómo simplifica WinInet la creación de aplicaciones cliente de Internet](../mfc/how-wininet-makes-it-easier-to-create-internet-client-applications.md)

