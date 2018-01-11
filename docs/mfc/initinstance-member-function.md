---
title: "Función miembro InitInstance | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: InitInstance
dev_langs: C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 96042b4d2931fb3709f992f6e43e408c919fe014
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="initinstance-member-function"></a>InitInstance Member (Función)
El sistema operativo Windows permite ejecutar más de una copia o "instancia" de la misma aplicación. `WinMain`llamadas [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) cada vez que inicia una nueva instancia de la aplicación.  
  
 El estándar `InitInstance` implementación creada por el Asistente para aplicaciones MFC realiza las tareas siguientes:  
  
-   Como su acción central, crea las plantillas de documento que a su vez crean documentos, vistas y ventanas de marco. Para obtener una descripción de este proceso, consulte [creación de la plantilla de documento](../mfc/document-template-creation.md).  
  
-   Carga las opciones de archivo estándar desde un archivo .ini o el registro de Windows, incluidos los nombres de los archivos usados más recientemente.  
  
-   Registra una o varias plantillas de documento.  
  
-   Para una aplicación MDI, crea una ventana de marco principal.  
  
-   Procesa la línea de comandos para abrir un documento especificado en la línea de comandos o para abrir un documento nuevo y vacío.  
  
 Puede agregar su propio código de inicialización o modificar el código escrito por el asistente.  
  
> [!NOTE]
>  Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si se llama a [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) en su `InitInstance` invalidar, especifique `COINIT_APARTMENTTHREADED` (en lugar de `COINIT_MULTITHREADED`). Para obtener más información, vea PRB: aplicación MFC deja de responder cuando se inicializa la aplicación como un multiproceso apartamento (828643) en [http://support.microsoft.com/default.aspxscid=kb;en-us;828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
## <a name="see-also"></a>Vea también  
 [CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
