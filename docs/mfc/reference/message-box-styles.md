---
title: "Estilos de cuadro de mensaje | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MB_ICONQUESTION"
  - "MB_ICONINFORMATION"
  - "MB_DEFBUTTON2"
  - "MB_YESNO"
  - "MB_OKCANCEL"
  - "MB_TASKMODAL"
  - "MB_ICONEXCLAMATION"
  - "MB_OK"
  - "MB_DEFBUTTON3"
  - "MB_YESNOCANCEL"
  - "MB_APPLMODAL"
  - "MB_RETRYCANCEL"
  - "MB_DEFBUTTON1"
  - "MB_ABORTRETRYIGNORE"
  - "MB_SYSTEMMODAL"
  - "MB_ICONSTOP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MB_ABORTRETRYIGNORE (constante)"
  - "MB_APPLMODAL (constante)"
  - "MB_DEFBUTTON1 (constante)"
  - "MB_DEFBUTTON2 (constante)"
  - "MB_DEFBUTTON3 (constante)"
  - "MB_ICONEXCLAMATION (constante)"
  - "MB_ICONINFORMATION (constante)"
  - "MB_ICONQUESTION (constante)"
  - "MB_ICONSTOP (constante)"
  - "MB_OK (constante)"
  - "MB_OKCANCEL (constante)"
  - "MB_RETRYCANCEL (constante)"
  - "MB_SYSTEMMODAL (constante)"
  - "MB_TASKMODAL (constante)"
  - "MB_YESNO (constante)"
  - "MB_YESNOCANCEL (constante)"
  - "estilos de cuadro de mensaje"
ms.assetid: d87014c5-4ea4-4950-a27e-7bcdda67be7d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Estilos de cuadro de mensaje
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los estilos siguientes del cuadro de mensajes.  
  
## Tipos de Message\_Box  
  
-   El cuadro de mensaje de**MB\_ABORTRETRYIGNORE**The contiene tres pulsadores: El anulación, intente, y omite.  
  
-   El cuadro de mensaje de**MB\_OK**The contiene un mismo botón: ACEPTAR.  
  
-   El cuadro de mensaje de**MB\_OKCANCEL**The contiene dos pulsadores: ACEPTAR y cancelación.  
  
-   El cuadro de mensaje de**MB\_RETRYCANCEL**The contiene dos pulsadores: Try y cancelación.  
  
-   El cuadro de mensaje de**MB\_YESNO**The contiene dos pulsadores: Sí y no.  
  
-   El cuadro de mensaje de**MB\_YESNOCANCEL**The contiene tres pulsadores: Sí, no, y eliminar.  
  
## Modalidad de cuadro de mensaje  
  
-   El usuario de**MB\_APPLMODAL**The debe responder al cuadro de mensaje antes de continuar el trabajo en la ventana actual.  Sin embargo, el usuario puede pasar a las ventanas de otras aplicaciones y trabajo en esas ventanas.  El valor predeterminado es **MB\_APPLMODAL** si no se especifica **MB\_SYSTEMMODAL** ni **MB\_TASKMODAL** .  
  
-   Se suspenden las aplicaciones de**MB\_SYSTEMMODAL**Todo hasta que el usuario responde al cuadro de mensaje.  Los cuadros de mensaje Sistema\- modales se usan para notificar al usuario de los errores graves, potencialmente perjudiciales que requieren una atención inmediata y deben utilizarse con moderación.  
  
-   **MB\_TASKMODAL** Similar a **MB\_APPLMODAL**, pero no es útil en una aplicación de la clase de la Microsoft foundation class.  Este marcador se reserva para una aplicación o biblioteca de llamada que no tiene un identificador de ventana disponibles.  
  
## Iconos del cuadro de mensaje  
  
-   **MB\_ICONEXCLAMATION** un icono de signo de exclamación aparece en el cuadro de mensaje.  
  
-   **MB\_ICONINFORMATION** el ser el icono “” en un círculo aparezco en el cuadro de mensaje.  
  
-   El icono de signo de interrogación de**MB\_ICONQUESTION**A aparece en el cuadro de mensaje.  
  
-   El icono de parada\- signo de**MB\_ICONSTOP**A aparece en el cuadro de mensaje.  
  
## Botones predeterminados del cuadro de mensaje  
  
-   El botón de**MB\_DEFBUTTON1**El primero es el valor predeterminado.  Observe que el primer botón siempre es el valor predeterminado a menos que se especifique **MB\_DEFBUTTON2** o **MB\_DEFBUTTON3** .  
  
-   El botón de**MB\_DEFBUTTON2**No está en segundo lugar el valor predeterminado.  
  
-   El tercer botón de**MB\_DEFBUTTON3**Z es el valor predeterminado.  
  
## Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [AfxMessageBox](../Topic/AfxMessageBox.md)