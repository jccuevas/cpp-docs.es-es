---
title: "Características avanzadas, Asistente para aplicaciones MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.advanced
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: bb94e24657d16b2a3eda3a770c2b6ae734c6006f
ms.openlocfilehash: 9a291af4641742cd9b771c80a7ea0770fab6de06
ms.lasthandoff: 04/12/2017

---
# <a name="advanced-features-mfc-application-wizard"></a>Características avanzadas, Asistente para aplicaciones MFC
En este tema se muestran las opciones de algunas características adicionales de la aplicación, como la Ayuda, la compatibilidad con la impresión, etc. En cada sección, debe especificar la compatibilidad adicional con estas características avanzadas.  
  
 **Ayuda contextual (HTML)**  
 Genera un conjunto de archivos de Ayuda de la Ayuda contextual, disponible mediante el uso de un menú de ayuda y F1 o haciendo clic en un **ayuda** botón en un cuadro de diálogo. Para agregar la compatibilidad con la Ayuda, se necesita el compilador de ayuda. Si no tiene el compilador de ayuda, puede volver a ejecutar el programa de instalación para instalarlo.  
  
 Vea [ayuda HTML: ayuda contextual para los programas](../../mfc/html-help-context-sensitive-help-for-your-programs.md) y [archivos de ayuda (Ayuda HTML)](../../ide/help-files-html-help.md) para obtener más información.  
  
 **Vista previa de impresión y**  
 Genera el código para controlar la impresión, imprimir el programa de instalación y comandos de vista previa de impresión mediante una llamada a funciones miembro el [CView (clase)](../../mfc/reference/cview-class.md) desde la biblioteca MFC. El asistente también agrega comandos para estas funciones al menú de la aplicación. Compatibilidad con la impresión solo está disponible para aplicaciones que especifiquen **compatibilidad con la arquitectura documento/vista** en el [tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md) página del asistente. De manera predeterminada, las aplicaciones de documento/vista son compatibles con la impresión.  
  
 **Automatización**  
 Especifica que la aplicación puede controlar objetos implementados en otra aplicación o expone la aplicación a clientes de Automation.  
  
 **Controles ActiveX**  
 Admite controles ActiveX (de forma predeterminada). Si no selecciona esta opción y posteriormente desea insertar controles ActiveX en el proyecto, debe agregar una llamada a [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) en la aplicación [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) función miembro.  
  
 **MAPI (API de mensajería)**  
 Especifica que la aplicación puede crear, manipular, transferir y almacenar mensajes de correo electrónico.  
  
 **Sockets de Windows**  
 Admite Windows Sockets, que se pueden usar para programar aplicaciones que se comuniquen a través de redes TCP/IP.  
  
 **Active Accessibility**  
 Agrega compatibilidad para [IAccessible](http://msdn.microsoft.com/library/windows/desktop/dd318466) a [CWnd](../../mfc/reference/cwnd-class.md)-las clases derivadas, que puede usar para personalizar la interfaz de usuario para una mejor interacción con los clientes de accesibilidad.  
  
 **Manifiesto de controles comunes**  
 Habilitado de manera predeterminada. Genera un manifiesto de aplicación que habilita el archivo DLL de controles comunes incluido con Microsoft Windows XP y sistemas operativos más recientes.  
  
 La versión 6 del archivo DLL de controles comunes no actualiza automáticamente la versión anterior de los controles comunes que se utilizan en las aplicaciones existentes. Para utilizar la versión 6 del archivo DLL de controles comunes, deberá crear un manifiesto de aplicación que indique a la aplicación que cargue el archivo DLL. Este archivo DLL de controles comunes admite también los temas de Windows XP.  
  
 Un manifiesto de aplicación puede especificar también otros archivos DLL y otras versiones que necesite la aplicación. Para obtener más información sobre los manifiestos de aplicación, consulte [aplicaciones aisladas y ensamblados en paralelo](http://msdn.microsoft.com/library/dd408052) en el [!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 **Compatibilidad con el Administrador de reinicio**  
 Agrega compatibilidad para la [Administrador de reinicio de Windows](http://msdn.microsoft.com/library/windows/desktop/aa373680\(v=vs.85\).aspx). Este vídeo muestra cómo usar el Administrador de reinicio de MFC: [Cómo: usar el nuevo administrador de reinicio](http://msdn.microsoft.com/vstudio/ee886407).  
  
 **Paneles de marco avanzados**  
 |Opción|Descripción|  
|------------|-----------------|  
|**Panel acoplable del explorador**|Crea un panel acoplable similar al de Visual Studio **el Explorador de soluciones** a la izquierda de la ventana de marco principal.|  
|**Marco acoplable de resultados**|Crea un panel acoplable similar al de Visual Studio **salida** panel que se encuentra en la ventana de marco principal.|  
|**Panel acoplable de propiedades**|Crea un panel acoplable similar al de Visual Studio **propiedades** panel situado a la derecha de la ventana de marco principal.|  
|**Panel de navegación**|Crea un panel acoplable similar a la barra de navegación de Outlook a la izquierda de la ventana del marco principal.|  
|**Barra de título**|Crea una barra de título similar a la de Office sobre la ventana del marco principal.|  
  
 **Número de archivos en la lista de archivos recientes**  
 Especifica el número de archivos que van a aparecer en la lista de archivos utilizados recientemente. El número predeterminado es 4.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)


