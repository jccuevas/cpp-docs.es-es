---
title: Alternativas a la arquitectura de documentos y vistas
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 98bb4de2f6d1a43fc1958a0fcbaafa1ac0af82a3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282557"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternativas a la arquitectura documento/vista

Aplicaciones MFC suelen usar la arquitectura documento/vista para administrar la información, formatos de archivo y la representación visual de datos a los usuarios. Para la mayoría de las aplicaciones de escritorio, la arquitectura documento/vista es una arquitectura de aplicación adecuados y eficaces. Esta arquitectura separa los datos de la vista y, en la mayoría de los casos, simplifica la aplicación y reduce el código redundante.

Sin embargo, la arquitectura documento/vista no es adecuada para algunas situaciones. Tenga en cuenta estos ejemplos:

- Si va a trasladar una aplicación escrita en C para Windows, puede completar su puerto antes de agregar compatibilidad documento/vista a la aplicación.

- Si está escribiendo una utilidad ligera, es posible que puede hacer sin la arquitectura documento/vista.

- Si el código original ya mezcla la administración de datos con datos viendo, mover el código al modelo documento/vista no es vale la pena porque debe separar los dos. Es preferible dejar el código tal cual.

Para crear una aplicación que no utiliza la arquitectura documento/vista, desactive la **compatibilidad con la arquitectura documento/vista** casilla de verificación en el paso 1 del Asistente para aplicaciones MFC. Consulte [MFC Application Wizard](../mfc/reference/mfc-application-wizard.md) para obtener más información.

> [!NOTE]
>  Aplicaciones basado en el cuadro de diálogo generadas por el Asistente para aplicaciones MFC no utilizan la arquitectura documento/vista, por lo que la **compatibilidad con la arquitectura documento/vista** casilla está deshabilitada si seleccionó el tipo de aplicación del cuadro de diálogo.

Los asistentes de Visual C++, así como los editores de código fuente y el cuadro de diálogo, trabajar con la aplicación generada tal como harían con cualquier otra aplicación generados por el asistente. La aplicación puede admitir las barras de herramientas, barras de desplazamiento y una barra de estado y tiene un **sobre** cuadro. La aplicación no registra ninguna plantilla de documento y no contendrá una clase de documento.

Tenga en cuenta que la aplicación generada tiene una clase de vista, `CChildView`, derivada de `CWnd`. MFC crea y coloca una instancia de la clase de vista dentro de las ventanas de marco creadas por la aplicación. MFC sigue exigiendo el uso de una ventana de vista, porque simplifica la colocación y administración de contenido de la aplicación. Puede agregar código de dibujo a la `OnPaint` miembro de esta clase. El código debería agregar barras de desplazamiento a la vista en lugar de en el marco.

Dado que la arquitectura documento/vista proporcionada por MFC es responsable de implementar muchas de las características básicas de una aplicación, su ausencia en el proyecto significa que usted es responsable de implementar muchas características importantes de la aplicación:

- Tal como lo proporciona el Asistente para aplicaciones MFC, el menú de la aplicación contiene sólo **New** y **Exit** comandos en el **archivo** menú. (El **New** comando solo se admite para las aplicaciones MDI, SDI no las aplicaciones sin documento/vista admiten.) El recurso de menú generado no será compatible con una lista MRU (usado más recientemente).

- Debe agregar funciones de controlador y las implementaciones para los comandos que será compatible con la aplicación, incluidos **abierto** y **guardar** en el **archivo** menú. MFC proporciona normalmente código para admitir estas características, pero esa compatibilidad está fuertemente enlazada a la arquitectura documento/vista.

- La barra de herramientas para la aplicación, si se solicitó una, será mínima.

Se recomienda encarecidamente usar al Asistente para aplicaciones MFC para crear aplicaciones sin la arquitectura documento/vista, dado que el asistente garantiza una arquitectura MFC correcta. Sin embargo, si se debe evitar mediante el asistente, aquí tiene varios enfoques para omitir la arquitectura documento/vista en el código:

- Tratar el documento como un apéndice sin usar e implementar el código de administración de datos en la clase de vista, como se sugirió anteriormente. Es relativamente baja sobrecarga para el documento. Una sola [CDocument](../mfc/reference/cdocument-class.md) objeto incurre en una pequeña cantidad de sobrecarga por sí mismo, además de la pequeña sobrecarga de `CDocument`de clases base, [CCmdTarget](../mfc/reference/ccmdtarget-class.md) y [CObject](../mfc/reference/cobject-class.md). Tanto de las últimas clases son pequeños.

   Declarado en `CDocument`:

  - Dos `CString` objetos.

  - Tres **BOOL**s.

  - Una `CDocTemplate` puntero.

  - Una `CPtrList` objeto, que contiene una lista de las vistas del documento.

  Además, el documento requiere que la cantidad de tiempo para crear el objeto de documento, sus objetos de vista, una ventana de marco y un objeto de plantilla de documento.

- Tratar el documento y la vista como apéndices no utilizados. Coloque el código de dibujo y administración de datos en la ventana de marco en lugar de la vista. Este enfoque está más cerca al modelo de programación de lenguaje C.

- Reemplace las partes de framework MFC que creación el documento y la vista para eliminar su creación en absoluto. El proceso de creación de documento comienza con una llamada a `CWinApp::AddDocTemplate`. Elimine esa llamada de la clase de aplicación `InitInstance` miembro de función y, en su lugar, cree una ventana de marco en `InitInstance` usted mismo. Coloque el código de administración de datos en la clase de ventana de marco. Se ilustra el proceso de creación de documento/vista en [creación de documento/vista](../mfc/document-view-creation.md). Esto supone más trabajo y requiere una comprensión más profunda de framework, pero libera completamente de la sobrecarga de documento/vista.

El artículo [MFC: Uso de las clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md) ofrece más ejemplos concretos de alternativas de documento/vista en el contexto de las aplicaciones de base de datos.

## <a name="see-also"></a>Vea también

[Arquitectura documento/vista](../mfc/document-view-architecture.md)
