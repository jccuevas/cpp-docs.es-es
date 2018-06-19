---
title: Procesamiento de bucles inactivos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, background processing
- PeekMessage method [MFC], elsewhere than message loop
- PeekMessage method [MFC]
- MFC, messages
- messages [MFC], loops
- OnIdle method [MFC]
- processing [MFC], background
- idle loop processing [MFC]
- idle processing [MFC]
- threading [MFC], alternatives to multithreading
- processing, during idle loop
- processing [MFC]
- background processing [MFC]
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d66983eb915c856ecf52e225b71151359a499b4b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354906"
---
# <a name="idle-loop-processing"></a>Procesamiento de bucles inactivos
Muchas aplicaciones realizan un procesamiento largo "en"segundo plano. A veces, las consideraciones de rendimiento dictan el uso del subprocesamiento múltiple para dicho trabajo. Subprocesos implican la labor de programación adicional, por lo que no se recomiendan para tareas sencillas, como el trabajo de tiempo de inactividad que realiza MFC en la [OnIdle](../mfc/reference/cwinthread-class.md#onidle) función. En este artículo se centra en el procesamiento en inactividad. Para obtener más información sobre el subprocesamiento múltiple, vea [temas de Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 Algunos tipos de procesamiento en segundo plano se realizan correctamente durante los intervalos que el usuario no interactúa con la aplicación. En una aplicación desarrollada para el sistema operativo Microsoft Windows, una aplicación puede realizar el procesamiento en tiempo de inactividad al dividir un proceso largo en muchos pequeños fragmentos. Después de procesar cada fragmento, la aplicación genera un control de ejecución para Windows mediante un [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) bucle.  
  
 Este artículo explica dos formas de procesamiento en inactividad en la aplicación:  
  
-   Usar **PeekMessage** en bucle de mensajes principal de MFC.  
  
-   Incrustar otro **PeekMessage** bucle en otro lugar en la aplicación.  
  
##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a> PeekMessage en el bucle de mensajes MFC  
 En una aplicación desarrollada con MFC, el mensaje principal un bucle en el `CWinThread` clase contiene un bucle de mensajes que llama el [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) API de Win32. Esto también bucle llama el `OnIdle` función miembro de `CWinThread` entre los mensajes. Una aplicación puede procesar mensajes en este tiempo de inactividad reemplazando la `OnIdle` función.  
  
> [!NOTE]
>  **Ejecutar**, `OnIdle`, y algunas otras funciones miembro son ahora miembros de clase `CWinThread` en lugar de la clase `CWinApp`. La clase `CWinApp` se deriva de la clase `CWinThread`.  
  
 Para obtener más información acerca de cómo realizar el procesamiento en inactividad, vea [OnIdle](../mfc/reference/cwinthread-class.md#onidle) en el *referencia de MFC*.  
  
##  <a name="_core_peekmessage_elsewhere_in_your_application"></a> PeekMessage en otra parte de la aplicación  
 Otro método para llevar a cabo en una aplicación de procesamiento en inactividad implica la incrustación de un bucle de mensajes en uno de sus funciones. Este bucle de mensajes es muy similar al bucle de mensajes principal de MFC, se encuentra en [CWinThread:: Run](../mfc/reference/cwinthread-class.md#run). Esto significa que un bucle de este tipo en una aplicación desarrollada con MFC, debe realizar muchas de las mismas funciones que el bucle de mensajes principal. El fragmento de código siguiente muestra cómo escribir un bucle de mensajes que es compatible con MFC:  
  
 [!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]  
  
 Este código, incrustado en una función, crea un bucle mientras hay procesamiento en inactividad. Dentro de ese bucle, un bucle anidado llama repetidamente **PeekMessage**. Siempre que esa llamada devuelve un valor distinto de cero, el bucle llama a `CWinThread::PumpMessage` para realizar la traducción de mensaje normal y distribución. Aunque `PumpMessage` está documentado, puede examinar su código fuente en el archivo ThrdCore.Cpp en el directorio \atlmfc\src\mfc de la instalación de Visual C++.  
  
 Una vez finaliza el bucle interno, el bucle externo realiza el procesamiento en inactividad con una o más llamadas a `OnIdle`. La primera llamada es para fines de MFC. Puede realizar llamadas adicionales `OnIdle` para realizar su propio trabajo en segundo plano.  
  
 Para obtener más información acerca de cómo realizar el procesamiento en inactividad, vea [OnIdle](../mfc/reference/cwinthread-class.md#onidle) en la referencia de la biblioteca MFC.  
  
## <a name="see-also"></a>Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)

