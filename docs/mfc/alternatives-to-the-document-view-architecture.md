---
title: Alternativas a la arquitectura de vista-documento
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 66325d1ae087b29f59f37197fb8695504bbddbc6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619758"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternativas a la arquitectura documento/vista

Normalmente, las aplicaciones MFC utilizan la arquitectura documento/vista para administrar la información, los formatos de archivo y la representación visual de los datos para los usuarios. Para la mayoría de las aplicaciones de escritorio, la arquitectura documento/vista es una arquitectura de aplicación adecuada y eficaz. Esta arquitectura separa los datos de la visualización y, en la mayoría de los casos, simplifica la aplicación y reduce el código redundante.

Sin embargo, la arquitectura documento/vista no es adecuada para algunas situaciones. Tenga en cuenta estos ejemplos:

- Si va a migrar una aplicación escrita en C para Windows, es posible que desee completar el puerto antes de agregar compatibilidad con el documento o la vista a la aplicación.

- Si está escribiendo una utilidad ligera, puede que le resulte más sencillo sin la arquitectura documento/vista.

- Si el código original ya mezcla la administración de datos con la visualización de datos, mover el código al modelo documento/vista no merece la pena el esfuerzo porque debe separar los dos. Es posible que prefiera dejar el código tal cual.

Para crear una aplicación que no use la arquitectura de documento/vista, desactive la casilla **compatibilidad con la arquitectura de documento/vista** en el paso 1 del Asistente para aplicaciones MFC. Consulte [Asistente para aplicaciones MFC](reference/mfc-application-wizard.md) para obtener más información.

> [!NOTE]
> Las aplicaciones basadas en cuadros de diálogo generadas por el Asistente para aplicaciones MFC no usan la arquitectura documento/vista, por lo que la casilla **compatibilidad con la arquitectura documento/vista** está deshabilitada si se selecciona el tipo de aplicación de cuadro de diálogo.

Los asistentes para Visual C++, así como los editores de origen y de diálogo, funcionan con la aplicación generada del mismo modo que con cualquier otra aplicación generada por el asistente. La aplicación puede admitir barras de herramientas, barras de desplazamiento y una barra de estado, y tiene un cuadro **acerca de** . La aplicación no registrará ninguna plantilla de documento y no contendrá una clase de documento.

Tenga en cuenta que la aplicación generada tiene una clase de vista, `CChildView` , derivada de `CWnd` . MFC crea y coloca una instancia de la clase de vista dentro de las ventanas de marco creadas por la aplicación. MFC sigue aplicándose mediante una ventana de vista, ya que simplifica la colocación y administración del contenido de la aplicación. Puede agregar código de dibujo al `OnPaint` miembro de esta clase. El código debe agregar barras de desplazamiento a la vista, en lugar de al marco.

Dado que la arquitectura de documento/vista proporcionada por MFC es responsable de implementar muchas de las características básicas de una aplicación, su ausencia en el proyecto significa que usted es responsable de implementar muchas características importantes de la aplicación:

- Tal y como lo proporciona el Asistente para aplicaciones MFC, el menú de la aplicación solo contiene los comandos **nuevo** y **salir** en el menú **archivo** . (El **nuevo** comando solo se admite para aplicaciones MDI, no para aplicaciones SDI sin soporte técnico de documento/vista). El recurso de menú generado no será compatible con una lista MRU (usados más recientemente).

- Debe agregar funciones de controlador e implementaciones para cualquier comando que admita la aplicación, incluidos **abrir** y **Guardar** en el menú **archivo** . Normalmente, MFC proporciona código para admitir estas características, pero esa compatibilidad está estrechamente enlazada a la arquitectura documento/vista.

- La barra de herramientas de la aplicación, si se ha solicitado una, será mínima.

Se recomienda encarecidamente que use el Asistente para aplicaciones MFC para crear aplicaciones sin la arquitectura documento/vista, ya que el asistente garantiza una arquitectura MFC correcta. Sin embargo, si debe evitar el uso del asistente, estos son varios métodos para omitir la arquitectura de documento/vista en el código:

- Trate el documento como un appendage sin usar e implemente el código de administración de datos en la clase de vista, tal y como se indicó anteriormente. La sobrecarga del documento es relativamente baja. Un solo objeto [CDocument](reference/cdocument-class.md) incurre en una pequeña cantidad de sobrecarga, además de la pequeña sobrecarga de `CDocument` las clases base de, [CCmdTarget](reference/ccmdtarget-class.md) y [CObject](reference/cobject-class.md). Las dos últimas clases son pequeñas.

   Declarado en `CDocument` :

  - Dos `CString` objetos.

  - Tres **bool**s.

  - Un `CDocTemplate` puntero.

  - Un `CPtrList` objeto, que contiene una lista de las vistas del documento.

  Además, el documento requiere la cantidad de tiempo para crear el objeto de documento, sus objetos de vista, una ventana de marco y un objeto de plantilla de documento.

- Trate el documento y la vista como appendages sin usar. Coloque el código de administración y dibujo de datos en la ventana de marco en lugar de en la vista. Este enfoque está más cerca del modelo de programación del lenguaje C.

- Reemplace las partes del marco de trabajo de MFC que crean el documento y la vista para eliminar su creación. El proceso de creación del documento comienza con una llamada a `CWinApp::AddDocTemplate` . Elimine esa llamada de la función miembro de la clase de la aplicación `InitInstance` y, en su lugar, cree una ventana de marco `InitInstance` . Coloque el código de administración de datos en la clase de ventana de marco. El proceso de creación de documentos y vistas se muestra en [creación de documentos y vistas](document-view-creation.md). Esto es más trabajo y requiere una comprensión más profunda de la plataforma, pero le libera por completo de la sobrecarga de documento/vista.

El artículo [MFC: usar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md) proporciona ejemplos más concretos de alternativas de documento o vista en el contexto de las aplicaciones de base de datos.

## <a name="see-also"></a>Consulte también

[Arquitectura documento/vista](document-view-architecture.md)
