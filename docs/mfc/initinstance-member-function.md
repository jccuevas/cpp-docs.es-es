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
ms.openlocfilehash: c1f83f794cc40fa7f4d290fa4a147fe9f7e074be
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508368"
---
# <a name="initinstance-member-function"></a>InitInstance Member (Función)

El sistema operativo Windows le permite ejecutar más de una copia de la misma aplicación, o "instancia". `WinMain`llama a [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) cada vez que se inicia una nueva instancia de la aplicación.

La implementación `InitInstance` estándar creada por el Asistente para aplicaciones MFC realiza las siguientes tareas:

- Como acción central, crea las plantillas de documento que, a su vez, crean documentos, vistas y ventanas de marco. Para obtener una descripción de este proceso, consulte [creación de plantillas de documentos](../mfc/document-template-creation.md).

- Carga las opciones de archivo estándar desde un archivo. ini o el registro de Windows, incluidos los nombres de los archivos usados más recientemente.

- Registra una o varias plantillas de documento.

- En el caso de una aplicación MDI, crea una ventana de marco principal.

- Procesa la línea de comandos para abrir un documento especificado en la línea de comandos o para abrir un nuevo documento vacío.

Puede agregar su propio código de inicialización o modificar el código escrito por el asistente.

> [!NOTE]
>  Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si llama a [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) en la `InitInstance` invalidación, especifique COINIT_APARTMENTTHREADED (en lugar de COINIT_MULTITHREADED).

## <a name="see-also"></a>Vea también

[CWinApp: La clase Application](../mfc/cwinapp-the-application-class.md)
