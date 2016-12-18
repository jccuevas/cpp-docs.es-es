---
title: "Asistente para controles ActiveX MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.ctl.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], MFC"
  - "Asistente para controles ActiveX MFC"
  - "controles ActiveX en MFC [C++], controles wizard"
  - "controles OLE [C++]"
  - "controles OLE [C++], crear"
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asistente para controles ActiveX MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un control ActiveX es un tipo específico de [servidor de automatización](../../mfc/automation-servers.md); es un componente reutilizable.  La aplicación que hospeda el control ActiveX es el [cliente de automatización](../../mfc/automation-clients.md) del control.  Si su objetivo es crear un componente reutilizable de este tipo, debe utilizar este asistente para crear el control.  Para obtener más información, vea [Controles ActiveX MFC](../../mfc/mfc-activex-controls.md).  
  
 Como alternativa, puede crear una aplicación MFC de servidor de automatización mediante el [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md).  
  
 Un control ActiveX creado con este asistente puede tener una interfaz de usuario o, por el contrario, ser invisible.  Puede especificar esta opción en la página [Configuración del control](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) del asistente.  Un ejemplo de control ActiveX que debería ser invisible es el control Timer.  
  
 Los controles ActiveX pueden tener una interfaz de usuario compleja.  Algunos controles pueden ser equivalentes a formularios encapsulados: un control individual que contiene muchos campos, siendo cada uno de ellos un control de Windows por derecho propio.  Por ejemplo, un objeto de piezas de automóvil implementado como un control ActiveX MFC podría presentar una interfaz de usuario de tipo formulario en la que los usuarios puedan leer y modificar el número de pieza, el nombre de la pieza y otros datos.  Para obtener más información, vea [Controles ActiveX MFC](../../mfc/mfc-activex-controls.md).  
  
 Si tiene que crear un contenedor para sus objetos ActiveX, vea [Crear un contenedor de controles ActiveX](../../mfc/reference/creating-an-mfc-activex-control-container.md).  
  
 El programa MFC inicial incluye archivos de origen de C\+\+ \(.cpp\), archivos de recursos \(.rc\) y un archivo de proyecto \(.vcxproj\).  El código generado en estos archivos iniciales se basa en MFC.  
  
 La siguiente lista de ejemplos muestra tareas y tipos de mejoras para el control ActiveX:  
  
-   [Optimizar un control ActiveX](../../mfc/mfc-activex-controls-optimization.md)  
  
-   [Agregar eventos estándar a un control ActiveX](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [Agregar eventos personalizados](../../mfc/mfc-activex-controls-adding-custom-events.md)  
  
-   [Agregar métodos estándar](../../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [Agregar métodos personalizados](../../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [Agregar propiedades estándar](../../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [Agregar propiedades personalizadas](../../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [Programar controles ActiveX en un contenedor de controles ActiveX](../../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
## Información general  
 En esta página del asistente se describe la configuración actual del proyecto de control ActiveX MFC que está creando.  De forma predeterminada, el asistente crea un proyecto de la manera siguiente:  
  
-   El proyecto predeterminado no genera ninguna licencia en tiempo de ejecución ni archivos de ayuda.  Puede modificar esta configuración predeterminada en la página [configuración de la aplicación](../../mfc/reference/application-settings-mfc-activex-control-wizard.md).  En la página **Información general** sólo se reflejarán las opciones que elija en esta página del Asistente para controles ActiveX.  
  
-   Este proyecto incluye una clase de control y una clase de página de propiedades cuyos nombres se basan en el nombre del proyecto.  Puede modificar los nombres del proyecto y los nombres de archivo en la página [Nombres del control](../../mfc/reference/control-names-mfc-activex-control-wizard.md).  
  
-   El control no se basa en ningún control de Windows existente y se activa cuando pasa a ser visible, tiene interfaz de usuario e incluye un cuadro de diálogo **Acerca de**.  Puede modificar esta configuración predeterminada en la página [configuración del control](../../mfc/reference/control-settings-mfc-activex-control-wizard.md).  
  
## Vea también  
 [Creación y administración de proyectos de Visual C\+\+](../../ide/creating-and-managing-visual-cpp-projects.md)   
 [Tipos de proyecto de Visual C\+\+](../../ide/visual-cpp-project-types.md)   
 [Conceptos](../../atl/active-template-library-atl-concepts.md)