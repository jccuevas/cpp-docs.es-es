---
title: Clases de documentos y de vistas creadas por el Asistente para aplicaciones MFC
ms.date: 11/04/2016
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
ms.openlocfilehash: 766fe4efb37c199c5babb75ce2cb08ebf676cca6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616053"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>Clases de documentos y de vistas creadas por el Asistente para aplicaciones MFC

El Asistente para aplicaciones MFC le ofrece un inicio principal en el desarrollo del programa mediante la creación de clases de documento y vista esquemáticas. A continuación, puede [asignar comandos y mensajes a estas clases](reference/mapping-messages-to-functions.md) y usar el editor de código fuente de Visual C++ para escribir sus funciones miembro.

La clase de documento creada por el Asistente para aplicaciones MFC se deriva de la clase [CDocument](reference/cdocument-class.md). La clase de vista se deriva de [CView](reference/cview-class.md). Los nombres que el Asistente para aplicaciones proporciona a estas clases y los archivos que los contienen se basan en el nombre del proyecto que se proporciona en el cuadro de diálogo Asistente para aplicaciones. En el Asistente para aplicaciones, puede usar la página clases generadas para modificar los nombres predeterminados.

Es posible que algunas aplicaciones necesiten más de una clase de documento, una clase de vista o una clase de ventana de marco. Para obtener más información, vea [varios tipos de documentos, vistas y ventanas de marco](multiple-document-types-views-and-frame-windows.md).

## <a name="see-also"></a>Consulte también

[Arquitectura documento/vista](document-view-architecture.md)
