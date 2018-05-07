---
title: Asistente para controles ActiveX MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.overview
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45af43a98244e90f52075817fc9e17a905cbf065
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-control-wizard"></a>Asistente para controles ActiveX MFC
Un control ActiveX es un tipo específico de [del servidor de automatización](../../mfc/automation-servers.md); es un componente reutilizable. La aplicación que hospeda el control ActiveX es el [cliente de automatización](../../mfc/automation-clients.md) de ese control. Si su objetivo es crear un componente reutilizable de ese tipo, a continuación, use este asistente para crear el control. Vea [controles ActiveX MFC](../../mfc/mfc-activex-controls.md) para obtener más información.  
  
 Como alternativa, puede crear una automatización de la aplicación de server MFC usando la [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md).  
  
 Un control ActiveX creado con este asistente puede tener una interfaz de usuario, o puede ser invisible. Puede especificar esta opción en el [configuración del Control](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) página del asistente. Un control timer es un ejemplo de un control ActiveX que podría desear ser invisible.  
  
 Controles ActiveX pueden tener una interfaz de usuario complejas. Algunos controles pueden ser equivalentes a formularios encapsulados: un control individual que contiene muchos campos, cada uno de ellos un control de Windows en su propio derecha. Por ejemplo, un objeto de partes automática implementado como un control ActiveX de MFC podría presentar una interfaz de usuario de forma similar a través del cual los usuarios podían leer y editar el número de pieza, nombre de una parte y otra información. Vea [controles ActiveX MFC](../../mfc/mfc-activex-controls.md) para obtener más información.  
  
 Si tiene que crear un contenedor para sus objetos ActiveX, vea [crear un contenedor de controles ActiveX](../../mfc/reference/creating-an-mfc-activex-control-container.md).  
  
 El programa MFC inicial incluye archivos de origen (.cpp) de C++, archivos de recursos (.rc) y un archivo de proyecto (.vcxproj). El código generado en estos archivos iniciales se basa en MFC.  
  
 En la lista de ejemplo siguiente muestra las tareas y los tipos de mejoras para el control ActiveX:  
  
-   [Optimizar un Control ActiveX](../../mfc/mfc-activex-controls-optimization.md)  
  
-   [Agregar eventos estándar a un Control ActiveX](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [Agregar eventos personalizados](../../mfc/mfc-activex-controls-adding-custom-events.md)  
  
-   [Agregar métodos estándar](../../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [Agregar métodos personalizados](../../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [Agregar propiedades estándar](../../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [Agregar propiedades personalizadas](../../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [Programar controles ActiveX en un contenedor de controles ActiveX](../../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
## <a name="overview"></a>Información general  
 Esta página del asistente describe la configuración de la aplicación actual para el proyecto de control ActiveX de MFC que está creando. De forma predeterminada, el asistente crea un proyecto de la manera siguiente:  
  
-   El proyecto predeterminado no genera ningún archivo de ayuda o licencia de tiempo de ejecución. Puede cambiar estos valores predeterminados en el [configuración de la aplicación](../../mfc/reference/application-settings-mfc-activex-control-wizard.md) página. Solo las selecciones que realice en esta página del Asistente de Control ActiveX se reflejan en el **Introducción** página.  
  
-   El proyecto incluye una clase de control y una clase de página de propiedades, según el nombre del proyecto. Puede editar los nombres de los nombres de archivo y el proyecto en el [nombres de los controles](../../mfc/reference/control-names-mfc-activex-control-wizard.md) página.  
  
-   El control se basa en ningún control de Windows existente y se activa cuando se vuelve visible, tiene una interfaz de usuario e incluye un **sobre** cuadro de diálogo. Puede cambiar estos valores predeterminados en el [configuración del Control](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) página.  
  
## <a name="see-also"></a>Vea también  
 [Creación y administración de proyectos de Visual C++](../../ide/creating-and-managing-visual-cpp-projects.md)   
 [Tipos de proyecto de Visual C++](../../ide/visual-cpp-project-types.md)   
 [Conceptos](../../atl/active-template-library-atl-concepts.md)

