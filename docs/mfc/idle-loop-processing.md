---
title: "Procesamiento de bucles inactivos | Microsoft Docs"
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
  - "procesamiento en segundo plano"
  - "procesamiento de bucles inactivos"
  - "procesamiento inactivo"
  - "mensajes, bucles"
  - "MFC, procesamiento en segundo plano"
  - "MFC, mensajes"
  - "OnIdle (método)"
  - "PeekMessage (método)"
  - "PeekMessage (método), en otro lugar que no sea el bucle de mensajes"
  - "procesar"
  - "procesar, fondo"
  - "procesar, durante el bucle inactivo"
  - "subprocesamiento [MFC], alternativas a subprocesamiento múltiple"
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Procesamiento de bucles inactivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muchas aplicaciones realizan el procesamiento largo “en segundo plano”. Las consideraciones de rendimiento dictan a veces con multithreading para este tipo de trabajo.  Los subprocesos la sobrecarga adicional implican ellas de desarrollo, por lo que no se recomienda para las tareas simples como el tiempo de inactividad que MFC hace en la función de [OnIdle](../Topic/CWinThread::OnIdle.md) .  En este artículo se centra en el procesamiento inactivo.  Para obtener más información sobre multithreading, vea [Temas de multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 Algunas clases de procesamiento en segundo plano se realizan correctamente durante intervalos que el usuario no está interactuando de otra manera con la aplicación.  En una aplicación desarrollada para el sistema operativo Microsoft Windows, una aplicación puede realizar el procesamiento del tiempo de inactividad dividiendo un proceso largo en muchos pequeños fragmentos.  Después de procesar cada fragmento, la aplicación hace que el control de ejecución a Windows mediante un bucle de [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) .  
  
 En este artículo se explica dos maneras de hacer el procesamiento inactivo en la aplicación:  
  
-   Mediante **PeekMessage** en el bucle principal de MFC.  
  
-   Insertar otro bucle de **PeekMessage** en alguna otra parte de la aplicación.  
  
##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a> PeekMessage en el bucle de mensajes MFC  
 En una aplicación desarrollada con MFC, el bucle principal en la clase de `CWinThread` contiene un bucle de mensajes que llame a la API Win32 de [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) .  Este bucle también llama a la función miembro de `OnIdle` de `CWinThread` entre los mensajes.  Una aplicación puede procesar mensajes en este tiempo de inactividad reemplazando la función de `OnIdle` .  
  
> [!NOTE]
>  **Ejecutar**, `OnIdle`, y que otras funciones miembro ahora son miembros de la clase `CWinThread` en lugar de clase `CWinApp`.  `CWinApp` se deriva de `CWinThread`.  
  
 Para obtener más información sobre cómo realizar el procesamiento inactivo, vea [OnIdle](../Topic/CWinThread::OnIdle.md) en *la referencia de MFC*.  
  
##  <a name="_core_peekmessage_elsewhere_in_your_application"></a> PeekMessage Elsewhere en la aplicación de El  
 Otro método para realizar el procesamiento inactivo en una aplicación implica la inserción de un bucle de mensajes en una de las funciones.  Este bucle de mensajes es muy similar al bucle principal de MFC, que se encuentra en [CWinThread::Run](../Topic/CWinThread::Run.md).  Eso significa que este bucle en una aplicación desarrollada con MFC debe realizar muchas de las mismas funciones que el bucle principal.  El fragmento de código siguiente muestra la escritura de un bucle de mensajes compatible con MFC:  
  
 [!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/CPP/idle-loop-processing_1.cpp)]  
  
 Este código, incrustado en una función, bucles mientras haya procesamiento inactivo a hacer.  Dentro del bucle, un bucle anidado llama repetidamente **PeekMessage**.  Siempre que esa llamada devuelve un valor distinto de cero, el bucle llama `CWinThread::PumpMessage` para realizar la traducción normal y enviar el mensaje.  Aunque `PumpMessage` es indocumentado, puede examinar el código fuente en el archivo de ThrdCore.Cpp en el directorio de \\atlmfc\\src\\mfc de la instalación de Visual C\+\+.  
  
 Una vez finaliza internos del bucle, el bucle exterior realizan el procesamiento inactivo con una o más llamadas a `OnIdle`.  La primera llamada es para fines de MFC.  Puede realizar llamadas adicionales a `OnIdle` para hacer dispone del trabajo en segundo plano.  
  
 Para obtener más información sobre cómo realizar el procesamiento inactivo, vea [OnIdle](../Topic/CWinThread::OnIdle.md) en la referencia de la biblioteca MFC.  
  
## Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)