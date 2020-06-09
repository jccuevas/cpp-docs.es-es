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
ms.openlocfilehash: c5beed5618d4fa991160ad1688a5a686aeaa842f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626367"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Inicializar y limpiar documentos y vistas

Utilice las siguientes directrices para inicializar y limpiar después de sus documentos y vistas:

- El marco de trabajo de MFC inicializa documentos y vistas; se inicializan los datos que se agregan a ellos.

- El marco de trabajo se limpia a medida que se cierran documentos y vistas; debe desasignar cualquier memoria asignada en el montón desde las funciones miembro de esos documentos y vistas.

> [!NOTE]
> Recuerde que la inicialización de toda la aplicación se realiza mejor en la invalidación de la función miembro [InitInstance](reference/cwinapp-class.md#initinstance) de la clase `CWinApp` , y la limpieza para toda la aplicación se realiza mejor en la invalidación de la `CWinApp` función miembro [ExitInstance](reference/cwinapp-class.md#exitinstance).

El ciclo de vida de un documento (y su ventana de marco y vista o vistas) en una aplicación MDI es el siguiente:

1. Durante la creación dinámica, se llama al constructor del documento.

1. Para cada nuevo documento, se llama a [OnNewDocument](reference/cdocument-class.md#onnewdocument) o [OnOpenDocument](reference/cdocument-class.md#onopendocument) del documento.

1. El usuario interactúa con el documento a lo largo de su duración. Normalmente esto sucede cuando el usuario trabaja en los datos del documento a través de la vista, seleccionando y editando los datos. La vista pasa los cambios al documento para el almacenamiento y la actualización de otras vistas. Durante este tiempo, el documento y la vista pueden controlar comandos.

1. El marco de trabajo llama a [DeleteContents](reference/cdocument-class.md#deletecontents) para eliminar los datos específicos de un documento.

1. Se llama al destructor del documento.

En una aplicación SDI, el paso 1 se realiza una vez, cuando se crea el documento por primera vez. Después, los pasos del 2 al 4 se realizan varias veces cada vez que se abre un nuevo documento. El nuevo documento reutiliza el objeto de documento existente. Por último, el paso 5 se realiza cuando finaliza la aplicación.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Inicialización de documentos y vistas](initializing-documents-and-views.md)

- [Limpiar documentos y vistas](cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Consulte también

[Arquitectura documento/vista](document-view-architecture.md)
