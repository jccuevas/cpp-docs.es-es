---
title: Crear una aplicación MFC basada en formularios | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcforms.project
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5ee588d7fe90e5bfc39aa8e4ab7a7499b62ad98
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372452"
---
# <a name="creating-a-forms-based-mfc-application"></a>Crear una aplicación MFC basada en formularios
Un formulario es un cuadro de diálogo con controles que permiten a un usuario tener acceso a datos y, posiblemente, modificarlos. Es posible que quiera desarrollar una aplicación en la que el usuario elija entre un conjunto de formularios. Normalmente, una aplicación basada en formularios permite a los formularios de acceso de usuario haciendo clic en **New** desde el **archivo** menú. Una aplicación basada en cuadros de diálogo, que no ofrece a los usuarios acceso a una **New** opción en el **archivo** menú, también se considera una aplicación basada en formularios.  
  
 Una aplicación basada en formularios de interfaz de un único documento (SDI) sólo permite que se ejecute una instancia de un formulario concreto cada vez. Es posible ejecutar formularios distintos al mismo tiempo desde una aplicación de basada en formularios SDI si selecciona un formulario nuevo de la **New** opción en el **archivo** menú.  
  
 Si crea una aplicación basada en formularios de interfaz de múltiples documentos (MDI), la aplicación permitirá el uso de varias instancias del mismo formulario.  
  
 Si crea una aplicación que admita varios documentos de nivel superior, el escritorio será la ventana primaria implícita del documento y el marco del documento no se restringirá al área de cliente de la aplicación. Puede abrir varias instancias del documento, cada una con su marco, su menú y su icono de la barra de tareas. Puede cerrar las instancias siguientes de los documentos de forma individual, pero si selecciona el `Exit` opción desde el **archivo** menú de la instancia inicial, la aplicación cierra todas las instancias.  
  
 Las aplicaciones SDI, MDI y de múltiples documentos de nivel superior son todas aplicaciones basadas en formularios y utilizan la arquitectura documento/vista.  
  
 Cualquier aplicación basada en un cuadro de diálogo es, por definición, una aplicación basada en formularios. Una aplicación basada en un cuadro de diálogo no utiliza la arquitectura documento/vista, por lo que el programador deberá administrar los métodos de creación y acceso para sus propios formularios adicionales.  
  
 La clase base para las aplicaciones basadas en formularios es [CFormView](../../mfc/reference/cformview-class.md). Si la aplicación ofrece compatibilidad con bases de datos, también puede seleccionar cualquier clase que se derive de `CFormView`. Un formulario es cualquier ventana derivada de `CFormView` o de cualquier clase que herede de `CFormView`.  
  
 Incluso si utiliza una clase base como [CView](../../mfc/reference/cview-class.md), podrá convertir posteriormente sus aplicaciones basadas en formularios [agregando una clase MFC](../../mfc/reference/adding-an-mfc-class.md) derivado de `CFormView` y comprobando la **generar DocTemplate recursos** casilla de verificación en la [Asistente para clases MFC](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md).  
  
 Cuando finalice el asistente, se abrirá el proyecto y, si seleccionó `CFormView` (o una clase que herede de `CFormView`) como clase base o creó una aplicación basada en un cuadro de diálogo, Visual C++ abrirá el editor de cuadros de diálogo. En este momento ya está preparado para diseñar su primer formulario.  
  
### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>Para empezar a crear un ejecutable MFC basado en formularios  
  
1.  Siga las instrucciones de [crear una aplicación MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  En el Asistente para aplicaciones MFC [tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) página, seleccione la **compatibilidad con la arquitectura documento/vista** casilla de verificación.  
  
3.  Seleccione **único documento**, **varios documentos**, o **varios documentos de nivel superior**.  
  
    > [!NOTE]
    >  Si elige una SDI, MDI o aplicación de interfaz de múltiples documentos de nivel superior, de forma predeterminada, `CView` se establece como la clase base para la vista de la aplicación en el [clases generadas](../../mfc/reference/generated-classes-mfc-application-wizard.md) página del asistente. Para crear una aplicación basada en formularios, debe seleccionar `CFormView` como clase base de la vista de la aplicación. Tenga en cuenta que el asistente no proporciona compatibilidad con la impresión para una aplicación basada en formularios.  
  
4.  Establezca las demás opciones de proyecto que desee en las otras páginas del asistente.  
  
5.  Haga clic en **finalizar** para generar la aplicación esqueleto.  
  
 Para obtener más información, consulte:  
  
-   [Clases de vista derivadas](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Alternativas a la arquitectura documento/vista](../../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [Opciones de diseño de aplicaciones](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Vistas de formulario](../../mfc/form-views-mfc.md)   
 [Crear una aplicación de MFC estilo Explorador de archivos](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)   
 [Creación de una aplicación MFC estilo explorador web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

