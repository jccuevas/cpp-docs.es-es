---
title: Alternativas a la arquitectura de vista-documento | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 459383474c9ffed9a7ad6cefe01ea21626cb23b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternativas a la arquitectura documento/vista
Aplicaciones MFC suelen usar la arquitectura documento/vista para administrar la información, formatos de archivo y la representación visual de los datos a los usuarios. Para la mayoría de las aplicaciones de escritorio, la arquitectura documento/vista es una arquitectura de aplicaciones adecuada y eficaz. Esta arquitectura separa los datos de la vista y, en la mayoría de los casos, simplifica la aplicación y reduce el código redundante.  
  
 Sin embargo, la arquitectura documento/vista no es adecuada en algunas situaciones. Tenga en cuenta estos ejemplos:  
  
-   Si va a trasladar una aplicación escrita en C para Windows, puede completar el puerto antes de agregar compatibilidad documento/vista para la aplicación.  
  
-   Si está escribiendo una utilidad sencilla, es posible que puede realizar sin la arquitectura documento/vista.  
  
-   Si el código original ya mezcla administración de datos con datos ver, mover el código al modelo documento/vista no es la pena porque debe separar los dos. Es preferible dejar el código tal cual.  
  
 Para crear una aplicación que no utiliza la arquitectura documento/vista, desactive el **compatibilidad con la arquitectura documento/vista** casilla de verificación en el paso 1 del Asistente para aplicaciones MFC. Vea [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) para obtener más información.  
  
> [!NOTE]
>  Aplicaciones basada en cuadros de diálogo generadas por el Asistente para aplicaciones MFC no utilizan la arquitectura documento/vista, por lo que la **compatibilidad con la arquitectura documento/vista** casilla está deshabilitada si seleccionó el tipo de aplicación del cuadro de diálogo.  
  
 Los asistentes de Visual C++, así como los editores de código fuente y cuadro de diálogo, trabajar con la aplicación generada igual que lo harían con cualquier otra aplicación generados por el asistente. La aplicación puede admitir barras de herramientas, barras de desplazamiento y una barra de estado y tiene un **sobre** cuadro. La aplicación no registrará las plantillas de documento y no contendrá una clase de documento.  
  
 Tenga en cuenta que la aplicación generada tiene una clase de vista, **CChildView**, derivado del `CWnd`. MFC crea y coloca una instancia de la clase de vista dentro de las ventanas de marco creadas por la aplicación. MFC sigue exigiendo el uso de una ventana de vista, porque simplifica la colocación y administrar el contenido de la aplicación. También puede agregar código de dibujo a la `OnPaint` miembro de esta clase. El código debería agregar barras de desplazamiento a la vista en lugar de al marco.  
  
 Dado que la arquitectura documento/vista proporcionada por MFC es responsable de implementar muchas de las características básicas de una aplicación, su ausencia en el proyecto significa que usted es responsable de implementar muchas características importantes de la aplicación:  
  
-   Proporcionados por el Asistente para aplicaciones MFC, el menú de la aplicación contiene solo `New` y `Exit` comandos en el **archivo** menú. (El `New` comando solo se admite para las aplicaciones MDI, no en aplicaciones SDI sin documento/vista admiten.) El recurso de menú generado no admitirá una lista de elementos utilizados Recientemente (usado más recientemente).  
  
-   Debe agregar funciones controladoras e implementaciones para los comandos que admita la aplicación, incluidos los **abiertos** y **guardar** en el **archivo** menú. MFC proporciona normalmente código para admitir estas características, pero esa compatibilidad está estrechamente relacionada a la arquitectura documento/vista.  
  
-   La barra de herramientas para la aplicación, si se solicitó una, será mínima.  
  
 Se recomienda encarecidamente utilizar al Asistente para aplicaciones MFC para crear aplicaciones sin la arquitectura documento/vista, ya que el asistente garantiza una arquitectura MFC correcta. Sin embargo, si se debe evitar mediante el asistente, aquí tiene varios enfoques para omitir la arquitectura documento/vista en el código:  
  
-   Tratar el documento como un apéndice no utilizado e implemente el código de administración de datos en la clase de vista, como se indica anteriormente. Sobrecarga para el documento es relativamente baja. Una sola [CDocument](../mfc/reference/cdocument-class.md) objeto incurre en una pequeña cantidad de sobrecarga por sí solo, además de la mínima sobrecarga de **CDocument**de clases base, [CCmdTarget](../mfc/reference/ccmdtarget-class.md) y [ CObject](../mfc/reference/cobject-class.md). Tanto las últimas clases son pequeñas.  
  
     Declarado en **CDocument**:  
  
    -   Dos `CString` objetos.  
  
    -   Tres **BOOL**s.  
  
    -   Una `CDocTemplate` puntero.  
  
    -   Una `CPtrList` objeto, que contiene una lista de las vistas del documento.  
  
     Además, el documento requiere que la cantidad de tiempo para crear el objeto de documento, sus objetos de vista, una ventana de marco y un objeto de plantilla de documento.  
  
-   Trate el documento y la vista como apéndices no utilizados. Coloque el código de dibujo y administración de datos en la ventana de marco en lugar de la vista. Este enfoque es más cercano para el modelo de programación de lenguaje C.  
  
-   Reemplace las partes del marco de trabajo MFC que crean el documento y la vista para eliminar su creación en absoluto. El proceso de creación de documento comienza con una llamada a `CWinApp::AddDocTemplate`. Elimine esa llamada de la clase de aplicación `InitInstance` miembro de función y, en su lugar, cree una ventana de marco en `InitInstance` usted mismo. Coloque el código de administración de datos en la clase de ventana de marco. El proceso de creación de documento/vista se muestra en [creación de documento/vista](../mfc/document-view-creation.md). Esto es más trabajo y requiere una comprensión más profunda de framework, pero le libera completamente de la sobrecarga de documento/vista.  
  
 El artículo [MFC: utilizar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md) ofrece más ejemplos concretos de alternativas de documento/vista en el contexto de las aplicaciones de base de datos.  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura documento/vista](../mfc/document-view-architecture.md)

