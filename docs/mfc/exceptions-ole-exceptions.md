---
title: "Excepciones: Excepciones OLE | Microsoft Docs"
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
  - "control de excepciones, OLE"
  - "excepciones, OLE"
  - "excepciones OLE"
  - "excepciones OLE, clases de control"
  - "OLE, excepciones"
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Excepciones: Excepciones OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las técnicas y funciones para administrar excepciones en OLE son iguales que las de administrar otras excepciones.  Para obtener más información sobre el control de excepciones, vea el artículo [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md).  
  
 Todos los objetos de excepción se derivan de la clase base abstracta `CException`.  MFC proporciona dos clases para administrar excepciones VIEJAS:  
  
-   [COleException](../mfc/reference/coleexception-class.md) For que administra excepciones general de OLE.  
  
-   [COleDispatchException](../mfc/reference/coledispatchexception-class.md) For que genera y que administra excepciones VIEJAS de envío \(automatización\).  
  
 La diferencia entre estas dos clases es la cantidad de información que proporcionan y donde se utilizan.  `COleException` tiene un miembro de datos público que contenga el código de estado OLE para la excepción.  fuentes de`COleDispatchException` más información, incluidos los siguientes:  
  
-   Un código de error específico de la aplicación  
  
-   Una descripción del error, como “disco lleno”  
  
-   Un contexto de Ayuda que la aplicación puede utilizar para proporcionar información adicional para el usuario  
  
-   El nombre del archivo de Ayuda de la aplicación  
  
-   El nombre de la aplicación que generó la excepción  
  
 `COleDispatchException` proporciona más información para que se pueda utilizar con productos como Microsoft Visual Basic.  La descripción de error verbal se puede utilizar en el cuadro de mensaje u otra notificación; información de Ayuda se puede utilizar para ayudar a responder a las condiciones que produjo la excepción.  
  
 Dos funciones globales corresponden a las dos clases de excepción VIEJAS: [AfxThrowOleException](../Topic/AfxThrowOleException.md) y [AfxThrowOleDispatchException](../Topic/AfxThrowOleDispatchException.md).  Utilícelos para producir excepciones VIEJAS de general y excepciones VIEJAS send, respectivamente.  
  
## Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)