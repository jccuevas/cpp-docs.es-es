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
ms.openlocfilehash: b02d5a1862a278f46591895f20f58a97367b5ab2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618798"
---
# <a name="framework-mfc"></a>Marco (MFC)

Su trabajo con el marco de biblioteca de Microsoft Foundation Class (MFC) se basa en gran medida en algunas clases principales y en varias herramientas de Visual C++. Algunas clases encapsulan una gran parte de la interfaz de programación de aplicaciones (API) de Win32. Otras clases encapsulan conceptos de aplicaciones como documentos, vistas y la propia aplicación. Otras personas encapsulan las características OLE y la funcionalidad de acceso a datos de ODBC y DAO.  (DAO es compatible con Office 2013. DAO 3,6 es la versión final y se considera obsoleta.)

Por ejemplo, la clase MFC encapsula Win32 concepto de ventana `CWnd` . Es decir, una clase de C++ denominada `CWnd` encapsula o "ajusta" el `HWND` identificador que representa una ventana de Windows. Del mismo modo, la clase `CDialog` encapsula los cuadros de diálogo de Win32.

La encapsulación significa que la clase `CWnd` de C++, por ejemplo, contiene una variable miembro de tipo `HWND` , y las funciones miembro de la clase encapsulan llamadas a funciones de Win32 que toman `HWND` como parámetro. Las funciones miembro de clase suelen tener el mismo nombre que la función de Win32 que encapsulan.

## <a name="in-this-section"></a>En esta sección

[SDI y MDI](sdi-and-mdi.md)

[Documentos, vistas y el marco de trabajo](documents-views-and-the-framework.md)

[Asistentes y editores de recursos](wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>En secciones relacionadas

[Compilar en el marco](building-on-the-framework.md)

[Cómo el marco llama al código](how-the-framework-calls-your-code.md)

[CWinApp: la clase Application](cwinapp-the-application-class.md)

[Plantillas de documento y el proceso de creación de documentos y vistas](document-templates-and-the-document-view-creation-process.md)

[Control y asignación de mensajes](message-handling-and-mapping.md)

[Window (Objetos)](window-objects.md)

## <a name="see-also"></a>Consulte también

[Uso de las clases para escribir aplicaciones para Windows](using-the-classes-to-write-applications-for-windows.md)
