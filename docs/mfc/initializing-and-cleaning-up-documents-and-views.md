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
ms.openlocfilehash: 3c92d60941cd6542bd0d6c27e8a879dc85e3a3d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377202"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Inicializar y limpiar documentos y vistas

Utilice las siguientes pautas para inicializar y limpiar después de sus documentos y vistas:

- El marco de trabajo MFC inicializa documentos y vistas; inicializa los datos que agregue a ellos.

- El marco de trabajo se limpia a medida que los documentos y las vistas se cierran; debe desasignar cualquier memoria que haya asignado en el montón desde dentro de las funciones miembro de esos documentos y vistas.

> [!NOTE]
> Recuerde que la inicialización de toda la aplicación se realiza mejor `CWinApp`en la invalidación de la función `CWinApp` miembro [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) de la clase y la limpieza de toda la aplicación se realiza mejor en la invalidación de la función miembro [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance).

El ciclo de vida de un documento (y su ventana de marco y vista o vistas) en una aplicación MDI es el siguiente:

1. Durante la creación dinámica, se llama al constructor del documento.

1. Para cada nuevo documento, se llama al [documento OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) o [OnOpenDocument.](../mfc/reference/cdocument-class.md#onopendocument)

1. El usuario interactúa con el documento a lo largo de su vida útil. Normalmente, esto sucede cuando el usuario trabaja en datos de documento a través de la vista, seleccionando y editando los datos. La vista pasa los cambios al documento para almacenar y actualizar otras vistas. Durante este tiempo, tanto el documento como la vista pueden controlar los comandos.

1. El marco de trabajo llama a [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) para eliminar datos específicos de un documento.

1. Se llama al destructor del documento.

En una aplicación SDI, el paso 1 se realiza una vez, cuando se crea el documento por primera vez. A continuación, los pasos 2 a 4 se realizan repetidamente cada vez que se abre un nuevo documento. El nuevo documento reutiliza el objeto de documento existente. Por último, el paso 5 se realiza cuando finaliza la aplicación.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Inicialización de documentos y vistas](../mfc/initializing-documents-and-views.md)

- [Limpiar documentos y vistas](../mfc/cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Consulte también

[Arquitectura de documento/vista](../mfc/document-view-architecture.md)
