---
title: Marco (MFC)
ms.date: 09/17/2019
helpviewer_keywords:
- encapsulation [MFC], Win32 API
- MFC, application framework
- wrapper classes [MFC], explained
- Win32 [MFC], API encapsulation by MFC
- application framework [MFC], about MFC application framework
- APIs [MFC], encapsulation by MFC Win32
- encapsulation [MFC]
- Windows API [MFC], encapsulation by MFC
- encapsulated Win32 API [MFC]
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
ms.openlocfilehash: 387f53e3123b6863fcf218da39c7c5e356eb8219
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303414"
---
# <a name="framework-mfc"></a>Marco (MFC)

Su trabajo con el marco de biblioteca de Microsoft Foundation Class (MFC) se basa en gran medida en algunas clases principales y C++ varias herramientas visuales. Algunas clases encapsulan una gran parte de la interfaz de programación de aplicaciones (API) de Win32. Otras clases encapsulan conceptos de aplicaciones como documentos, vistas y la propia aplicación. Otras personas encapsulan las características OLE y la funcionalidad de acceso a datos de ODBC y DAO.  (DAO es compatible con Office 2013. DAO 3,6 es la versión final y se considera obsoleta.)

Por ejemplo, Win32 concepto de ventana está encapsulado por la clase MFC `CWnd`. Es decir, una C++ clase denominada `CWnd` encapsula o "ajusta" el identificador de `HWND` que representa una ventana de Windows. Del mismo modo, la clase `CDialog` encapsula cuadros de diálogo Win32.

La encapsulación significa que C++ la clase `CWnd`, por ejemplo, contiene una variable miembro de tipo `HWND`y las funciones miembro de la clase encapsulan llamadas a funciones de Win32 que toman un `HWND` como parámetro. Las funciones miembro de clase suelen tener el mismo nombre que la función de Win32 que encapsulan.

## <a name="in-this-section"></a>En esta sección

[SDI y MDI](../mfc/sdi-and-mdi.md)

[Documentos, vistas y el marco](../mfc/documents-views-and-the-framework.md)

[Asistentes y editores de recursos](../mfc/wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>En secciones relacionadas

[Compilación en el marco](../mfc/building-on-the-framework.md)

[Cómo el marco llama al código](../mfc/how-the-framework-calls-your-code.md)

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)

[Plantillas de documento y el proceso de creación de documentos y vistas](../mfc/document-templates-and-the-document-view-creation-process.md)

[Control y asignación de mensajes](../mfc/message-handling-and-mapping.md)

[Objetos de ventana](../mfc/window-objects.md)

## <a name="see-also"></a>Vea también

[Uso de las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
