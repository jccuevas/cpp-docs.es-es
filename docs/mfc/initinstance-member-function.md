---
title: Función miembro InitInstance | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- InitInstance
dev_langs:
- C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9379fef6a1d676d6a3bc757ee51d5d27acd5f6f
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930181"
---
# <a name="initinstance-member-function"></a>InitInstance Member (Función)
El sistema operativo Windows permite ejecutar más de una copia o "instancia" de la misma aplicación. `WinMain` llamadas [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) cada vez que inicia una nueva instancia de la aplicación.  
  
 El estándar `InitInstance` implementación creada por el Asistente para aplicaciones MFC realiza las tareas siguientes:  
  
-   Como su acción central, crea las plantillas de documento que a su vez crean documentos, vistas y ventanas de marco. Para obtener una descripción de este proceso, consulte [creación de la plantilla de documento](../mfc/document-template-creation.md).  
  
-   Carga las opciones de archivo estándar desde un archivo .ini o el registro de Windows, incluidos los nombres de los archivos usados más recientemente.  
  
-   Registra una o varias plantillas de documento.  
  
-   Para una aplicación MDI, crea una ventana de marco principal.  
  
-   Procesa la línea de comandos para abrir un documento especificado en la línea de comandos o para abrir un documento nuevo y vacío.  
  
 Puede agregar su propio código de inicialización o modificar el código escrito por el asistente.  
  
> [!NOTE]
>  Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si se llama a [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) en su `InitInstance` invalidar, especifique COINIT_APARTMENTTHREADED (en lugar de COINIT_MULTITHREADED). Para obtener más información, vea PRB: aplicación MFC deja de responder cuando se inicializa la aplicación como un multiproceso apartamento (828643) en [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
## <a name="see-also"></a>Vea también  
 [CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
