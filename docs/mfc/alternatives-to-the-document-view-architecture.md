---
title: Alternativas a la arquitectura Document-View
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 41af30d25d7ddb9e2bdbb7a0f7b86cb741ae1048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370800"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternativas a la arquitectura documento/vista

Las aplicaciones MFC normalmente usan la arquitectura de documento/vista para administrar información, formatos de archivo y la representación visual de datos para los usuarios. Para la mayoría de las aplicaciones de escritorio, la arquitectura de documento/vista es una arquitectura de aplicación adecuada y eficiente. Esta arquitectura separa los datos de la visualización y, en la mayoría de los casos, simplifica la aplicación y reduce el código redundante.

Sin embargo, la arquitectura de documento/vista no es adecuada para algunas situaciones. Considere estos ejemplos:

- Si va a migrar una aplicación escrita en C para Windows, es posible que desee completar el puerto antes de agregar compatibilidad con documentos o vistas a la aplicación.

- Si está escribiendo una utilidad ligera, es posible que pueda prescindir de la arquitectura de documento/vista.

- Si el código original ya mezcla la administración de datos con la visualización de datos, mover el código al modelo de documento/vista no vale la pena el esfuerzo porque debe separar los dos. Es posible que prefiera dejar el código tal como está.

Para crear una aplicación que no utilice la arquitectura de documento/vista, desactive la casilla de verificación **Compatibilidad con la arquitectura Document/View** en el paso 1 del Asistente para aplicaciones MFC. Consulte [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) para obtener más información.

> [!NOTE]
> Las aplicaciones basadas en cuadros de diálogo generadas por el Asistente para aplicaciones MFC no utilizan la arquitectura de documento/vista, por lo que la casilla de verificación Compatibilidad con **la arquitectura Document/View** está deshabilitada si selecciona el tipo de aplicación de cuadro de diálogo.

Los asistentes de Visual C++, así como los editores de código fuente y diálogo, funcionan con la aplicación generada del igual que lo harían con cualquier otra aplicación generada por el asistente. La aplicación puede admitir barras de herramientas, barras de desplazamiento y una barra de estado, y tiene un cuadro **Acerca** de. La aplicación no registrará ninguna plantilla de documento y no contendrá una clase de documento.

Tenga en cuenta que la aplicación `CChildView`generada tiene `CWnd`una clase de vista, , derivada de . MFC crea y coloca una instancia de la clase de vista dentro de las ventanas de marco creadas por la aplicación. MFC sigue obligando mediante una ventana de vista, ya que simplifica el posicionamiento y la administración del contenido de la aplicación. Puede agregar código de `OnPaint` pintura al miembro de esta clase. El código debe agregar barras de desplazamiento a la vista en lugar de al marco.

Dado que la arquitectura de documento/vista proporcionada por MFC es responsable de implementar muchas de las características básicas de una aplicación, su ausencia en el proyecto significa que es responsable de implementar muchas características importantes de la aplicación:

- Según lo proporcionado por el Asistente para aplicaciones MFC, el menú de la aplicación solo contiene comandos **New** y **Exit** en el menú **Archivo.** (El comando **Nuevo** solo se admite para aplicaciones MDI, no para aplicaciones SDI sin compatibilidad con documentos/vistas.) El recurso de menú generado no admitirá una lista MRU (utilizada más recientemente).

- Debe agregar funciones e implementaciones de controlador para los comandos que admita la aplicación, incluidos **Abrir** y **Guardar** en el menú **Archivo.** MFC normalmente proporciona código para admitir estas características, pero esa compatibilidad está estrechamente enlazada a la arquitectura de documento/vista.

- La barra de herramientas de la aplicación, si ha solicitado una, será mínima.

Se recomienda encarecidamente que utilice el Asistente para aplicaciones MFC para crear aplicaciones sin la arquitectura de documento/vista, ya que el asistente garantiza una arquitectura MFC correcta. Sin embargo, si debe evitar el uso del asistente, aquí hay varios enfoques para omitir la arquitectura de documento/vista en el código:

- Trate el documento como un apéndice no utilizado e implemente el código de administración de datos en la clase de vista, como se sugirió anteriormente. La sobrecarga del documento es relativamente baja. Un único [cDocument](../mfc/reference/cdocument-class.md) objeto incurre en una pequeña cantidad `CDocument`de sobrecarga por sí mismo, además de la pequeña sobrecarga de 's clases base, [CCmdTarget](../mfc/reference/ccmdtarget-class.md) y [CObject](../mfc/reference/cobject-class.md). Ambas clases son pequeñas.

   Declarado `CDocument`en :

  - Dos `CString` objetos.

  - Tres **BOOL**s.

  - Un `CDocTemplate` puntero.

  - Un `CPtrList` objeto, que contiene una lista de las vistas del documento.

  Además, el documento requiere la cantidad de tiempo para crear el objeto de documento, sus objetos de vista, una ventana de marco y un objeto de plantilla de documento.

- Trate tanto el documento como la vista como apéndices no utilizados. Coloque el código de dibujo y administración de datos en la ventana de marco en lugar de en la vista. Este enfoque está más cerca del modelo de programación en lenguaje C.

- Invalide las partes del marco MFC que crean el documento y la vista para eliminar la creación de ellas en absoluto. El proceso de creación de `CWinApp::AddDocTemplate`documentos comienza con una llamada a . Elimine esa llamada de `InitInstance` la función miembro de la `InitInstance` clase de aplicación y, en su lugar, cree una ventana de marco en usted mismo. Coloque el código de administración de datos en la clase de ventana de marco. El proceso de creación de documento/vista se ilustra en [Creación de documento/vista](../mfc/document-view-creation.md). Esto es más trabajo y requiere una comprensión más profunda del marco de trabajo, pero le libera por completo de la sobrecarga de documento/vista.

El artículo MFC: Uso de clases de base de datos [sin documentos y vistas](../data/mfc-using-database-classes-without-documents-and-views.md) proporciona ejemplos más concretos de alternativas de documento y vista en el contexto de las aplicaciones de base de datos.

## <a name="see-also"></a>Consulte también

[Arquitectura de documento/vista](../mfc/document-view-architecture.md)
