---
title: Inicializar y limpiar documentos y vistas
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
ms.openlocfilehash: 7bfc80e636a3018e52dec411f17bdf25073cf4c2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584644"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Inicializar y limpiar documentos y vistas

Use las directrices siguientes para inicializar y limpiar después de los documentos y vistas:

- El marco de trabajo MFC inicializa documentos y vistas; inicializar los datos que se les agrega.

- El marco de trabajo limpia como documentos y vistas de cierre; debe desasignar la memoria asignada en el montón desde dentro de las funciones miembro de esos documentos y vistas.

> [!NOTE]
>  Recuerde que la inicialización para toda la aplicación se realiza mejor en el reemplazo del [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) función miembro de clase `CWinApp`, y limpieza para toda la aplicación se realiza mejor en el reemplazo del `CWinApp`función miembro [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance).

El ciclo de vida de un documento (y su ventana de marco y la vista o vistas) en los formularios MDI aplicación es como sigue:

1. Durante la creación dinámica, se llama al constructor de documento.

1. Para cada nuevo, el documento del documento [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) o [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) se llama.

1. El usuario interactúa con el documento durante su vigencia. Normalmente esto sucede cuando el usuario trabaja en datos del documento a través de la vista, seleccionar y editar los datos. La vista pasa cambios al documento para almacenar y actualizar otras vistas. Durante este tiempo, el documento y la vista podrían controlar comandos.

1. Las llamadas de framework [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) para eliminar los datos específicos de un documento.

1. Se llama el destructor del documento.

En una aplicación SDI, paso 1 se realiza una vez, cuando se crea por primera vez el documento. A continuación, los pasos 2 a 4 se realizan varias veces cada vez que se abre un nuevo documento. El nuevo documento vuelve a utilizar el objeto de documento existente. Por último, paso 5 se realiza cuando finaliza la aplicación.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Inicialización de documentos y vistas](../mfc/initializing-documents-and-views.md)

- [Limpieza de documentos y vistas](../mfc/cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Vea también

[Arquitectura documento/vista](../mfc/document-view-architecture.md)

