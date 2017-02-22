---
title: "Caracter&#237;sticas avanzadas, Asistente para aplicaciones MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.exe.advanced"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para aplicaciones MFC, características avanzadas"
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# Caracter&#237;sticas avanzadas, Asistente para aplicaciones MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se muestran las opciones de algunas características adicionales de la aplicación, como la Ayuda, la compatibilidad con la impresión, etc.  En cada sección, debe especificar la compatibilidad adicional con estas características avanzadas.  
  
 **Ayuda contextual \(HTML\)**  
 Genera un conjunto de archivos de ayuda contextual, disponibles a través la tecla F1 y un menú Ayuda, o bien haciendo clic en el botón **Ayuda** de un cuadro de diálogo.  Para agregar la compatibilidad con la Ayuda, se necesita el compilador de ayuda.  Si no tiene el compilador de ayuda, puede volver a ejecutar el programa de instalación para instalarlo.  
  
 Vea [Ayuda HTML: Ayuda contextual para los programas](../../mfc/html-help-context-sensitive-help-for-your-programs.md) y [Archivos de ayuda \(Ayuda HTML\)](../../ide/help-files-html-help.md) para obtener más información.  
  
 **Impresión y vista previa de impresión**  
 Genera el código necesario para controlar los comandos de impresión, configuración de la impresora y vista previa de impresión mediante llamadas a funciones miembro de la [CView Class](../../mfc/reference/cview-class.md) desde la biblioteca MFC.  El asistente también agrega comandos para estas funciones al menú de la aplicación.  La compatibilidad con la impresión solo está disponible para aplicaciones que indiquen su **compatibilidad con la arquitectura documento\/vista** en la página [Tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md) del asistente.  De manera predeterminada, las aplicaciones de documento\/vista son compatibles con la impresión.  
  
 **Automatización**  
 Especifica que la aplicación puede controlar objetos implementados en otra aplicación o expone la aplicación a clientes de automatización.  
  
 **Controles ActiveX**  
 Admite controles ActiveX \(de forma predeterminada\).  Si no selecciona esta opción y posteriormente desea insertar controles ActiveX en el proyecto, deberá agregar una llamada a [AfxEnableControlContainer](../Topic/AfxEnableControlContainer.md) en la función miembro [CWinApp::InitInstance](../Topic/CWinApp::InitInstance.md) de la aplicación.  
  
 **MAPI \(API de mensajería\)**  
 Especifica que la aplicación puede crear, manipular, transferir y almacenar mensajes de correo electrónico.  
  
 **Windows Sockets**  
 Admite Windows Sockets, que se pueden usar para programar aplicaciones que se comuniquen a través de redes TCP\/IP.  
  
 **Active Accessibility**  
 Agrega compatibilidad con [IAccessible](http://msdn.microsoft.com/library/windows/desktop/dd318466) en las clases derivadas de [CWnd](../../mfc/reference/cwnd-class.md), lo que se puede utilizar para personalizar la interfaz de usuario para obtener una mejor interacción con los clientes de accesibilidad.  
  
 **Manifiesto de controles comunes**  
 Habilitado de manera predeterminada.  Genera un manifiesto de aplicación que habilita el archivo DLL de controles comunes incluido con Microsoft Windows XP y sistemas operativos más recientes.  
  
 La versión 6 del archivo DLL de controles comunes no actualiza automáticamente la versión anterior de los controles comunes que se utilizan en las aplicaciones existentes.  Para utilizar la versión 6 del archivo DLL de controles comunes, deberá crear un manifiesto de aplicación que indique a la aplicación que cargue el archivo DLL.  Este archivo DLL de controles comunes admite también los temas de Windows XP.  
  
 Un manifiesto de aplicación puede especificar también otros archivos DLL y otras versiones que necesite la aplicación.  Para obtener más información sobre los manifiestos de aplicación, vea el tema sobre [aplicaciones aisladas y ensamblados en paralelo](http://msdn.microsoft.com/library/dd408052) en [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)].  
  
 **Admitir Administrador de reinicio**  
 Agrega compatibilidad con el [Administrador de reinicio de Windows](http://msdn.microsoft.com/library/windows/desktop/aa373680\(v=vs.85\).aspx).  En este vídeo se muestra cómo utilizar el administrador de reinicio de MFC: [Cómo: Usar el nuevo administrador de reinicio.](http://msdn.microsoft.com/vstudio/ee886407).  
  
 **Paneles de marco avanzados**  
 |Opción|Descripción|  
|------------|-----------------|  
|**Panel acoplable del explorador**|Crea un panel acoplable similar al **Explorador de soluciones** de Visual Studio a la izquierda de la ventana del marco principal.|  
|**Marco acoplable de resultados**|Crea un panel acoplable similar al panel **Resultados** de Visual Studio debajo de la ventana del marco principal.|  
|**Panel acoplable de propiedades**|Crea un panel acoplable similar al panel **Propiedades** de Visual Studio a la derecha de la ventana del marco principal.|  
|**Panel de navegación**|Crea un panel acoplable similar a la barra de navegación de Outlook a la izquierda de la ventana del marco principal.|  
|**Barra de título**|Crea una barra de título similar a la de Office sobre la ventana del marco principal.|  
  
 **Número de archivos en la lista de archivos recientes**  
 Especifica el número de archivos que van a aparecer en la lista de archivos utilizados recientemente.  El número predeterminado es 4.  
  
## Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)