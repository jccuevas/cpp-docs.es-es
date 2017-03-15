---
title: "Windows Sockets: Convertir cadenas | Microsoft Docs"
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
  - "sockets [C++], problemas de conversión de cadena de carácter multibyte"
  - "conversión de cadenas, cadenas de carácter multibyte"
  - "Windows Sockets [C++], conversión de cadena de carácter multibyte"
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows Sockets: Convertir cadenas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este artículo y dos casos de acompañan explican varios aspectos de la programación de Windows Sockets.  Este artículo trata convertir cadenas.  Otros problemas se tratan en [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md) y [Windows Sockets: El orden de byte](../mfc/windows-sockets-byte-ordering.md).  
  
 Si usa o deriva de la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), deberá administrar estos problemas personalmente.  Si usa o deriva de la clase [CSocket](../mfc/reference/csocket-class.md), MFC los administra.  
  
## Convertir cadenas  
 Si se comunica entre las aplicaciones que usan cadenas almacenadas en diferentes formatos de carácter ancho, como Unicode o juegos de caracteres multibyte \(MBCS\), o entre una de estas y una aplicación mediante las cadenas de caracteres ANSI, debe administrar las conversiones usted mismo en `CAsyncSocket`.  El objeto de `CArchive` utilizado con un objeto de `CSocket` administra esta conversión automáticamente con las funciones de clase [CString](../atl-mfc-shared/reference/cstringt-class.md).  Para obtener más información, vea la especificación de Windows Sockets, establecida en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, vea:  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: En segundo plano](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Sockets de secuencia](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)