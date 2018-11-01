---
title: InitInstance Member (Función)
ms.date: 11/04/2016
f1_keywords:
- InitInstance
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
ms.openlocfilehash: 6e430d30dc62a14008fad9e41e3b2cde7ddffc8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450601"
---
# <a name="initinstance-member-function"></a>InitInstance Member (Función)

El sistema operativo Windows permite ejecutar más de una copia o "instancia" de la misma aplicación. `WinMain` las llamadas [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) cada vez que se inicia una nueva instancia de la aplicación.

El estándar `InitInstance` implementación creada por el Asistente para aplicaciones MFC realiza las siguientes tareas:

- Como su acción central, crea las plantillas de documento que a su vez crean documentos, vistas y ventanas de marco. Para obtener una descripción de este proceso, consulte [creación de plantillas de documento](../mfc/document-template-creation.md).

- Carga las opciones de archivo estándar desde un archivo .ini o el registro de Windows, incluidos los nombres de los archivos usados más recientemente.

- Registra una o varias plantillas de documento.

- Para una aplicación MDI, crea una ventana de marco principal.

- Procesa la línea de comandos para abrir un documento especificado en la línea de comandos o abrir un documento nuevo y vacío.

Puede agregar su propio código de inicialización o modificar el código escrito por el asistente.

> [!NOTE]
>  Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si se llama a [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) en su `InitInstance` invalidar, especifique COINIT_APARTMENTTHREADED (en lugar de COINIT_MULTITHREADED).

## <a name="see-also"></a>Vea también

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
