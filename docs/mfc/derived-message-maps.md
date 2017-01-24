---
title: "Mapas de mensajes derivados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas de mensajes derivados"
  - "control de mensajes, controladores de mensajes derivados"
  - "mapas de mensajes, derivadas"
  - "mensajes, enrutar"
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mapas de mensajes derivados
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Durante el control de mensajes, comprobar propio mapa de mensajes de una clase no es el fin del caso de mensaje\- mapa.  ¿Qué ocurre si la clase `CMyView` \(derivado de `CView`\) no tiene ninguna entrada correspondiente para un mensaje?  
  
 Tenga presente que `CView`, la clase base de `CMyView`, deriva a su vez de `CWnd`.  Así `CMyView` *es* `CView` y *es* `CWnd`.  Cada una de esas clases tiene su propio mapa de mensajes.  La figura “una jerarquía de vista” siguiente muestra la relación jerárquica de las clases, pero la tiene en cuenta que un objeto de `CMyView` es un solo objeto que tiene las características de las tres clases.  
  
 ![Jerarquía de una vista](../mfc/media/vc38621.png "vc38621")  
Una jerarquía de vista  
  
 Tan si un mensaje no se pueden buscar en mapa de mensajes de `CMyView` de clase, el marco también busca el mapa de mensajes de la clase base inmediata.  La macro de `BEGIN_MESSAGE_MAP` al principio del mapa de mensajes especifica dos nombres de clase como argumentos:  
  
 [!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/CPP/derived-message-maps_1.cpp)]  
  
 Los primeros nombres de argumento la clase a la que el mapa de mensajes pertenece.  El segundo argumento proporciona una conexión con la clase base inmediata — `CView` aquí — para que el marco puede buscar el mapa de mensajes, también.  
  
 La clase derivada se heredan los controladores de mensajes proporcionados en una clase base junto.  Esto es muy similar a las funciones virtuales normales de miembro sin necesidad todas las funciones miembro de controlador virtuales.  
  
 Si no se encuentra ningún controlador en mapas cualquiera de los del mensaje de la clase base, el procesamiento de mensajes predeterminado se realiza.  Si el mensaje es un comando, el marco se enrutan al destino de comando siguiente.  Si es un mensaje estándar de Windows, el mensaje se pasa al procedimiento de ventana predeterminado adecuado.  
  
 El mensaje\- mapa de velocidad que coincide, el marco almacena en caché coincidencias recientes en la probabilidad que recibirá el mismo mensaje.  Una consecuencia de esto es que el marco procesa mensajes no controlados muy eficaz.  Los mapas de mensajes también son espacio\- más eficaces que las implementaciones que utilizan funciones virtuales.  
  
## Vea también  
 [Cómo busca el marco los mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md)