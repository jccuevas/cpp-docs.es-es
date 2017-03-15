---
title: "Invalidar el enrutamiento de comandos est&#225;ndar | Microsoft Docs"
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
  - "control de comandos, comandos de enrutamiento"
  - "enrutamiento de comandos, reemplazar"
  - "MFC, enrutamiento de comandos"
  - "reemplazar, comandos de enrutamiento estándar"
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Invalidar el enrutamiento de comandos est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En casos raros debe implementar alguna variación de marco estándar que distribuye, puede invalidarlo.  La idea es cambiar el enrutamiento en una o más clases reemplazando `OnCmdMsg` en esas clases.  Hacerlo:  
  
-   En la clase importante el orden de a un objeto no predeterminado.  
  
-   En el nuevo objeto no predeterminado o en destinos de comando puede ser que a su vez pasar comandos a.  
  
 Si se inserta un nuevo objeto en el enrutamiento, la clase debe ser una clase de comando\- destino.  En las versiones que reemplazan de `OnCmdMsg`, asegúrese de llamar a la versión que está reemplazando.  Vea la función miembro de [OnCmdMsg](../Topic/CCmdTarget::OnCmdMsg.md) de la clase `CCmdTarget` en *la referencia de MFC* y las versiones en clases como `CView` y **CDocument** en el código fuente proporcionado para los ejemplos.  
  
## Vea también  
 [Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)