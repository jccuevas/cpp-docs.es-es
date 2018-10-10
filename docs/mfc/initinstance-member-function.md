---
title: Función miembro InitInstance | Microsoft Docs
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
ms.openlocfilehash: bc9d1d1ff35755a966591e6f46f7742ddfa59e08
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890028"
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
