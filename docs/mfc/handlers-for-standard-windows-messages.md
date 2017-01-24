---
title: "Controladores para mensajes est&#225;ndar de Windows | Microsoft Docs"
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
  - "afx_msg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones [C++], controlador"
  - "funciones controladoras, mensajes estándar de Windows"
  - "control de mensajes [C++], controladores de mensajes de Windows"
  - "mensajes [C++], Windows"
  - "mensajes de Windows [C++], controladores"
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controladores para mensajes est&#225;ndar de Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Predefinidas controladores predeterminados para los mensajes estándar de Windows \(**WM\_**\) en la clase `CWnd`.  La biblioteca de clases basa los nombres para estos controladores en el nombre del mensaje.  Por ejemplo, el controlador del mensaje de `WM_PAINT` en `CWnd` como:  
  
 `afx_msg void OnPaint();`  
  
 La palabra clave de **afx\_msg** sugiere el efecto de la palabra clave de C\+\+ **virtual** distinguiendo controladores de otras funciones miembro de `CWnd` .  Observe, sin embargo, que estas funciones no son realmente virtuales; en su lugar se implementan mediante mapas de mensajes.  Los mapas de mensajes dependen sólo de macro estándar preprocesador, no en cualquier extensión del lenguaje C\+\+.  La palabra clave de **afx\_msg** resuelve el espacio en blanco después del preprocesamiento.  
  
 Para reemplazar un controlador definido en una clase base, defina simplemente una función con el mismo prototipo en la clase derivada y crear una entrada de mensaje\- mapa para el controlador.  El controlador “reemplaza” cualquier controlador del mismo nombre en las clases base de la clase cualquiera de los.  
  
 En algunos casos, el controlador debe llamar al controlador reemplazado en la clase base para que la clase base y Windows pueden funcionar en el mensaje.  Cuando se llama al controlador de la clase base en la invalidación depende de las circunstancias.  Debe llamar a veces el controlador de la clase base primero y a veces por última vez.  Se llama a veces el controlador de la clase base condicional, si decide no procesar el mensaje personalmente.  Debe llamar a veces el controlador de la clase base, después condicional para ejecutarse dispone de código del controlador, dependiendo del valor o del estado devuelto por el controlador de la clase base.  
  
> [!CAUTION]
>  No es seguro modificar los argumentos pasados en un controlador si piensa pasarlos a un controlador de clases base.  Por ejemplo, podría verse tentado para modificar el argumento de `nChar` de controlador de `OnChar` \(convertir a mayúsculas, por ejemplo\).  Este comportamiento es bastante indeterminado, pero si necesita realizar este efecto, usa la función **SendMessage** miembro de `CWnd` en su lugar.  
  
 ¿Cómo se determina la manera adecuada de reemplazar un mensaje determinado?  Cuando la ventana Propiedades escribe la estructura de la función controladora para un mensaje determinado — controlador de `OnCreate` para `WM_CREATE`, por ejemplo — traza en forma de función invalidada recomendada del miembro.  El ejemplo siguiente se recomienda que la llamada del controlador primero el controlador de la clase base y continúa sólo con tal de que no vuelve a 1.  
  
 [!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/CPP/handlers-for-standard-windows-messages_1.cpp)]  
  
 Por convención, los nombres de estos controladores comienzan con el prefijo “en”. Algunos de estos controladores no toman ningún argumento, mientras que otros tienen varios.  Algunos también tienen un tipo de valor devuelto distinto de `void`.  Documentan controladores predeterminados para todos los mensajes de **WM\_** en *la referencia de MFC* como las funciones miembro de clases `CWnd` cuyos nombres comienzan por “en”. Las declaraciones de función miembro en `CWnd` llevan **afx\_msg**.  
  
## Vea también  
 [Declarar funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)