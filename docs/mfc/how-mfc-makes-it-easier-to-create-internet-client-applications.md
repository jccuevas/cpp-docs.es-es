---
title: "Cómo simplifica MFC crear aplicaciones de cliente de Internet | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f6270cdd3e64d24f1c2000acb9e8466f8c85edba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>Cómo simplifica MFC la creación de aplicaciones cliente de Internet
Microsoft Foundation Classes encapsular las funciones de extensión de Internet Win32 (WinInet) de forma que proporciona un contexto familiar para los programadores MFC. MFC proporciona tres clases de archivos de Internet ([CInternetFile](../mfc/reference/cinternetfile-class.md), [CHttpFile](../mfc/reference/chttpfile-class.md), y [CGopherFile](../mfc/reference/cgopherfile-class.md)) derivado de la [CStdioFile](../mfc/reference/cstdiofile-class.md) (clase) . No solo estas clases se realizan recuperar y manipular datos de Internet resultará familiar a los programadores que han usado `CStdioFile` para archivos locales, pero con estas clases pueden controlar archivos locales y los archivos de Internet de forma transparente.  
  
 Las clases WinInet de MFC proporcionan la misma funcionalidad que `CStdioFile` para los datos que se transfieren a través de Internet. Estas clases abstraen los protocolos de Internet para HTTP, FTP y gopher en una aplicación de alto nivel interfaz de programación, lo que proporciona una ruta de acceso rápido y sencillo para hacer que las aplicaciones basadas en Internet. Por ejemplo, conectarse a un servidor FTP todavía requiere varios pasos en un nivel bajo, pero como programador de MFC, basta con hacer una llamada a `CInternetSession::GetFTPConnection` para crear la conexión.  
  
 Además, las clases WinInet de MFC proporcionan las siguientes ventajas:  
  
-   Almacenado en búfer de E/S  
  
-   Identificadores de seguridad de tipos para los datos  
  
-   Parámetros predeterminados para muchas funciones  
  
-   Control de excepciones de errores comunes de Internet  
  
-   Limpieza automática de identificadores abiertos y conexiones  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Cómo simplifica WinInet la creación de aplicaciones cliente de Internet](../mfc/how-wininet-makes-it-easier-to-create-internet-client-applications.md)

