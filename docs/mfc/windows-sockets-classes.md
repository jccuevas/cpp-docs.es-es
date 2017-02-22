---
title: "Clases de Windows Sockets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.net"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de sockets"
  - "Windows Sockets [C++], clases"
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Clases de Windows Sockets
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El Windows Sockets proporciona una manera de la protocolo\- independiente de la red de comunicación entre dos equipos.  Estos sockets pueden ser sincrónicos \(el programa espera hasta que se realice la comunicación\) o asincrónico \(el programa continúa ejecutándose mientras está pasando la comunicación\).  
  
 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)  
 Encapsula el Windows Sockets API en un contenedor fino.  
  
 [CSocket](../mfc/reference/csocket-class.md)  
 Abstracción de alto nivel derivada de `CAsyncSocket`.  Funciona de forma sincrónica.  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 Proporciona una interfaz de `CFile` a un socket de Windows.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)