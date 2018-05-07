---
title: Crear una aplicación de MFC estilo Explorador de archivos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcexplorer.project
dev_langs:
- C++
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5b0f5d4bdabc987d4f4177f616ce756c351b8b5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>Crear una aplicación MFC estilo Explorador de archivos
Muchas aplicaciones de sistema de Windows utilizan la interfaz de usuario (UI) para el Explorador de archivos. Por ejemplo, cuando se inicia el Explorador de archivos, verá una aplicación con un vertical barra divisora que divide el área de cliente. El lado izquierdo del área de cliente proporciona características para explorar y exploración, y el lado derecho del área de cliente muestra los detalles relativos a la selección en el panel izquierdo. Cuando un usuario hace clic en un elemento en el panel izquierdo, la aplicación vuelve a rellenar el panel derecho. En una aplicación MDI, puede usar comandos en el **vista** menú para cambiar la cantidad de detalle que se muestra en el panel derecho. (En un SDI o aplicación de múltiples documentos de nivel superior, puede cambiar los detalles con los botones de barra de herramientas solo.)  
  
 El contenido de los paneles depende de la aplicación. En un explorador de sistema de archivos, el panel izquierdo muestra una vista jerárquica de directorios o equipos o grupos de equipos, mientras que el panel derecho muestra carpetas, archivos individuales, o máquinas y detalles acerca de ellos. El contenido no tiene necesariamente que ser archivos. Podrían ser mensajes de correo electrónico, informes de errores u otros elementos en una base de datos.  
  
 El asistente crea las siguientes clases para usted:  
  
-   El **CLeftView** clase define el panel izquierdo del área cliente. Siempre se deriva de [CTreeView](../../mfc/reference/ctreeview-class.md).  
  
-   La C*Nombre_proyecto*clase View define el panel derecho del área de cliente. De forma predeterminada, se deriva de [CListView](../../mfc/reference/clistview-class.md) , pero puede ser otro tipo de vista en función de la clase que especifique en el **clase Base** lista en la [clases generadas](../../mfc/reference/generated-classes-mfc-application-wizard.md) página de la Asistente.  
  
 La aplicación generada puede tener una interfaz de único documento (SDI), una interfaz de múltiples documentos (MDI) o una arquitectura de múltiples documentos de nivel superior. Cada ventana de marco que crea la aplicación se divide verticalmente mediante [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md). La codificación de este tipo de aplicación es similar a programar una aplicación MFC normal que utiliza un divisor, salvo que este tipo de aplicación tiene vistas de control independientes en cada panel divisor.  
  
 Si utiliza la vista de lista predeterminada en el panel derecho, el asistente crea las opciones de menú adicionales (en aplicaciones de MDI) y botones de barra de herramientas para cambiar el estilo de vista entre iconos grandes, iconos pequeños, lista y modos de detalle.  
  
### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>Para empezar a crear un ejecutable MFC estilo Explorador de archivos  
  
1.  Siga las instrucciones de [crear una aplicación MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  En el Asistente para aplicaciones MFC [tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) página, seleccione la **Explorador de archivos** estilo del proyecto.  
  
3.  Establezca las demás opciones que desee en las otras páginas del asistente.  
  
4.  Haga clic en **finalizar** para generar la aplicación esqueleto.  
  
 Para obtener más información, consulte:  
  
-   [Varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Clases de vista derivadas](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Opciones de diseño de aplicaciones](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Crear una aplicación de MFC estilo explorador Web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)   
 [Creación de una aplicación MFC basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md)

