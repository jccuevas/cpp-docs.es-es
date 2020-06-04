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
ms.openlocfilehash: 2cf5b266348e299fe761ba40bd2cfb849f02b9ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377194"
---
# <a name="initinstance-member-function"></a>InitInstance Member (Función)

El sistema operativo Windows le permite ejecutar más de una copia, o "instancia", de la misma aplicación. `WinMain`llama a [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) cada vez que se inicia una nueva instancia de la aplicación.

La `InitInstance` implementación estándar creada por el Asistente para aplicaciones MFC realiza las siguientes tareas:

- Como su acción central, crea las plantillas de documento que a su vez crean documentos, vistas y ventanas de marco. Para obtener una descripción de este proceso, consulte Creación de plantillas de [documento](../mfc/document-template-creation.md).

- Carga las opciones de archivo estándar desde un archivo .ini o el registro de Windows, incluidos los nombres de los archivos utilizados más recientemente.

- Registra una o más plantillas de documento.

- Para una aplicación MDI, crea una ventana de marco principal.

- Procesa la línea de comandos para abrir un documento especificado en la línea de comandos o para abrir un nuevo documento vacío.

Puede agregar su propio código de inicialización o modificar el código escrito por el asistente.

> [!NOTE]
> Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si llama a [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) en la invalidación, `InitInstance` especifique COINIT_APARTMENTTHREADED (en lugar de COINIT_MULTITHREADED).

## <a name="see-also"></a>Consulte también

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
