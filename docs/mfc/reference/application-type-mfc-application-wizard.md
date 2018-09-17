---
title: Tipo de aplicación, Asistente para aplicaciones MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.apptype
dev_langs:
- C++
helpviewer_keywords:
- static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f302c797dd1074bcd96385c7ec1552589853f127
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720699"
---
# <a name="application-type-mfc-application-wizard"></a>Tipo de aplicación, Asistente para aplicaciones MFC
Utilice esta página de la [MFC Application Wizard](../../mfc/reference/mfc-application-wizard.md) para diseñar y agregar características básicas a una nueva aplicación MFC.  
  
- **Tipo de aplicación**

   Especifica el tipo de compatibilidad de documentos que desea crear en la aplicación. El tipo de aplicación que seleccione determina las opciones de interfaz de usuario que están disponibles para su aplicación. Consulte [características de la interfaz de usuario, Asistente para aplicaciones MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md) para obtener más información.  
  
   Para obtener más información sobre los tipos de documentos, consulte:  
  
   - [SDI y MDI](../../mfc/sdi-and-mdi.md)  
  
   - [Ventanas de marco](../../mfc/frame-windows.md)  
  
   - [Clases de ventana de marco](../../mfc/frame-window-classes.md)  
  
   - [Documentos, vistas y el marco](../../mfc/documents-views-and-the-framework.md)  
  
   - [Cuadros de diálogo](../../mfc/dialog-boxes.md)  
  
   |Opción|Descripción|  
   |------------|-----------------|  
   |**Documento único**|Crea una arquitectura de único documento (SDI) de la interfaz para la aplicación, donde una clase de vista se basa en [clase CView](../../mfc/reference/cview-class.md). Puede cambiar la clase base para la vista en el [clases generadas, Asistente para aplicaciones MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) página del asistente. Para crear una aplicación basada en formularios, por ejemplo, use [clase CFormView](../../mfc/reference/cformview-class.md) para la clase de vista.<br /><br /> En este tipo de aplicación, la ventana de marco del documento puede contener solo un documento.|  
   |**Varios documentos**|Crea una arquitectura de múltiples documentos (MDI) de la interfaz de la aplicación, donde una clase de vista se basa en `CView`. Puede cambiar la clase base para la vista en el **clases generadas** página del asistente. Para crear una aplicación basada en formularios, por ejemplo, use `CFormView` para la clase de vista.<br /><br /> En este tipo de aplicación, ventana de marco del documento puede contener varias ventanas secundarias.|  
   |**Organización por pestañas**|Coloca cada documento en una pestaña independiente.|  
   |**En función del cuadro de diálogo**|Crea una arquitectura basada en el cuadro de diálogo para la aplicación que una clase de cuadro de diálogo se basa en `CDialog`. (Para crear un cuadro de diálogo HTML, active la casilla **diálogo usar HTML**.)|  
   |**Utilice el cuadro de diálogo HTML**|Cuadro de diálogo cuadro solo para aplicaciones. Derive la clase de cuadro de diálogo de [clase CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) en lugar de [CDialog (clase)](../../mfc/reference/cdialog-class.md). Si activa esta casilla, `CDHtmlDialog` aparece en el **clase Base** cuadro el [clases generadas, Asistente para aplicaciones MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) página del asistente.<br /><br /> Un `CDHtmlDialog`-cuadro de diálogo derivado muestra cuadros de diálogo basado en HTML, intercambia datos con HTML controlan y administra los eventos HTML.|  
   |**Varios documentos de nivel superior**|Crea una arquitectura de nivel superior múltiples para su aplicación, donde una clase de vista se basa en `CView`.<br /><br /> En este tipo de aplicación, cuando un usuario hace clic **New** (o **nuevo marco**) en el **archivo** menú, la aplicación crea una ventana cuyo elemento primario es implícitamente el escritorio. El nuevo marco de documento aparece en la barra de tareas y no está restringido al área de cliente de la ventana de la aplicación.|  
  
- **Compatibilidad con la arquitectura de documento/vista**

   Especifica si se debe incluir la arquitectura documento/vista en la aplicación mediante el [CDocument (clase)](../../mfc/reference/cdocument-class.md) y [CView (clase)](../../mfc/reference/cview-class.md) (valor predeterminado). Desactive esta casilla si va a trasladar una aplicación no basados en MFC o si desea reducir el tamaño del archivo ejecutable compilado. De forma predeterminada, se deriva de una aplicación sin la arquitectura documento/vista [CWinApp (clase)](../../mfc/reference/cwinapp-class.md), y no incluye compatibilidad con MFC para abrir un documento desde un archivo de disco.  
  
- **Idioma de recurso**

   Establece el idioma de los recursos. La lista muestra los idiomas disponibles en el sistema, como se instalan con Visual Studio. Si desea seleccionar un idioma distinto del idioma del sistema, ya debe instalarse la carpeta de plantilla adecuada para dicho idioma. Para obtener más información acerca de cómo instalar recursos de idiomas distintos de los valores predeterminados disponibles en la **idioma de recurso** lista, vea [compatibilidad del asistente con otros lenguajes](../../ide/wizard-support-for-other-languages.md).  
  
   El idioma que seleccione se refleja en el **cadenas traducidas** opción de la [cadenas de plantillas de documento, el Asistente para aplicaciones MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md) página del asistente.  
  
- **Uso de bibliotecas de Unicode**

   Especifica si se usa la versión de las bibliotecas MFC Unicode o no Unicode.  
  
- **Estilo de proyecto**

   Indica si la aplicación tiene un estándar MFC, Explorador de archivos, Visual Studio, o arquitectura de Office y mostrar. Para obtener más información, consulte [crear una aplicación de MFC estilo Explorador de archivos](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md).  
  
   |Opción|Descripción|  
   |------------|-----------------|  
   |**Estándar MFC**|Proporciona una arquitectura de aplicaciones de MFC estándar.|  
   |**Explorador de archivos**|Implementa una aplicación similar al explorador de archivos mediante el uso de una ventana divisora, donde es el panel izquierdo una [clase CTreeView](../../mfc/reference/ctreeview-class.md) y el panel derecho es un [CListView (clase)](../../mfc/reference/clistview-class.md).|  
   |**Visual Studio**|Implementa una aplicación de Visual Studio como que contiene cuatro paneles acoplables (**File View**, **vista de clases**, **propiedades**, y **salida**) que se derivan [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) y una ventana de marco principal que se deriva de [CMDIFrameWndEx (clase)](../../mfc/reference/cmdiframewndex-class.md) (valor predeterminado).|  
   |**Office**|Implementa una aplicación de Office como que contiene una cinta de opciones que se deriva de [CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md), una barra de Outlook que se deriva de [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md), una barra de título que se deriva de [CMFCCaptionBar (clase)](../../mfc/reference/cmfccaptionbar-class.md)y un marco principal que se deriva de [CMDIFrameWndEx (clase)](../../mfc/reference/cmdiframewndex-class.md).|  
  
- **Estilo visual y colores**

   Determina el estilo visual de la aplicación. Están disponibles las siguientes opciones:  
  
   - **Windows nativo/predeterminado**  
  
   - **Office 2003**  
  
   - **Visual Studio 2005**  
  
   - **Office 2007 (tema azul)**  
  
   - **Office 2007 (tema negro)**  
  
   - **Office 2007 (tema plateado)**  
  
   - **Office 2007 (tema aguamarina)**  
  
- **Habilitar el cambio de estilo visual**

   Especifica si el usuario puede cambiar el estilo visual de la aplicación en tiempo de ejecución, normalmente mediante la selección del estilo visual correspondiente en un menú o una cinta de opciones.  
  
- **Uso de MFC**

   Especifica cómo vincular a la biblioteca MFC. De forma predeterminada, MFC vinculada como un archivo DLL compartido.  
  
   |Opción|Descripción|  
   |------------|-----------------|  
   |**Utilizar MFC en un archivo DLL compartido**|Vincula la biblioteca MFC a una aplicación como un archivo DLL compartido. La aplicación realiza llamadas a la biblioteca MFC en tiempo de ejecución. Esta opción reduce los requisitos de disco y memoria de aplicaciones que constan de varios archivos ejecutables que utilizan la biblioteca MFC. Las aplicaciones de Win32 y MFC pueden llamar a funciones en el archivo DLL (valor predeterminado)|  
   |**Utilizar MFC en una biblioteca estática**|Vincula una aplicación a la biblioteca MFC estática en tiempo de compilación.|  
  
## <a name="see-also"></a>Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Tipos de archivos creados para proyectos de Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)

