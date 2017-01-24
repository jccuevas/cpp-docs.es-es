---
title: "C&#243;mo: Usar la referencia cruzada del mapa de mensajes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ventanas [C++], mapas de mensajes"
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Usar la referencia cruzada del mapa de mensajes
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En las entradas etiquetadas \<memberFxn\>, escriba por la función miembro de una clase derivada de [CWnd](../../mfc/reference/cwnd-class.md) .  Asigne a función cualquier nombre que desee.  Otras funciones, por ejemplo `OnActivate`, es funciones miembro de clases `CWnd`.  Si se invoca, se pasa el mensaje a la función de `DefWindowProc` Windows.  Para procesar los mensajes de notificación de Windows, reemplace la función correspondiente de `CWnd` en la clase derivada.  La función debe llamar a la función invalidada en la clase base para que la clase base y Windows responder al mensaje.  
  
 En todos los casos, el prototipo de función en `CWnd`\- el encabezado de la clase derivada, y el código el mensaje asignan entrada como se muestra.  
  
 Se utilizan los términos siguientes:  
  
|Término|Definición|  
|-------------|----------------|  
|id|Cualquier identificador de elemento de menú definido por el usuario \(mensajes de**WM\_COMMAND** \) o identificador del control \(mensajes de notificación de ventana secundaria\).|  
|“mensaje” y “wNotifyCode”|Identificadores de mensaje de Windows definido en WINDOWS.H.|  
|nMessageVariable|Nombre de una variable que contiene el valor devuelto de la función de **RegisterWindowMessage** Windows.|  
  
## Vea también  
 [Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)