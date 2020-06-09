---
title: Derivar una clase de documento de CDocument
ms.date: 11/04/2016
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
ms.openlocfilehash: 399230446977636cc8769efe32b8f86fad466b83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616119"
---
# <a name="deriving-a-document-class-from-cdocument"></a>Derivar una clase de documento de CDocument

Los documentos contienen y administran los datos de la aplicación. Para usar la clase de documento proporcionada por el Asistente para aplicaciones MFC, debe hacer lo siguiente:

- Derive una clase de `CDocument` para cada tipo de documento.

- Agregue variables de miembro para almacenar los datos de cada documento.

- Invalide `CDocument` `Serialize` la función miembro de la clase de documento. `Serialize`escribe y Lee los datos del documento a y desde el disco.

## <a name="other-document-functions-often-overridden"></a>Otras funciones de documento a menudo se invalidan

También puede que desee invalidar otras `CDocument` funciones miembro. En concreto, a menudo tendrá que invalidar [OnNewDocument](reference/cdocument-class.md#onnewdocument) y [OnOpenDocument](reference/cdocument-class.md#onopendocument) para inicializar los miembros de datos del documento y [DeleteContents](reference/cdocument-class.md#deletecontents) para destruir los datos asignados dinámicamente. Para obtener información sobre los miembros reemplazables, vea la clase [CDocument](reference/cdocument-class.md) en la *referencia de MFC*.

## <a name="see-also"></a>Consulte también

[Usar documentos](using-documents.md)
