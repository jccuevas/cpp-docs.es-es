---
title: Características avanzadas, Asistente para aplicaciones MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.advanced
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
ms.openlocfilehash: dc2b745bf97dff65a3612c29745c9d0e455a347d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507804"
---
# <a name="advanced-features-mfc-application-wizard"></a>Características avanzadas, Asistente para aplicaciones MFC

En este tema se muestran las opciones de algunas características adicionales de la aplicación, como la Ayuda, la compatibilidad con la impresión, etc. En cada sección, debe especificar la compatibilidad adicional con estas características avanzadas.

- **Ayuda contextual (HTML)**

   Genera un conjunto de archivos de ayuda para la ayuda contextual, disponible mediante F1 y un menú ayuda, o haciendo clic en un botón **ayuda** en un cuadro de diálogo. Para agregar la compatibilidad con la Ayuda, se necesita el compilador de ayuda. Si no tiene el compilador de ayuda, puede volver a ejecutar el programa de instalación para instalarlo.

   Vea [la ayuda HTML: Ayuda contextual para los programas](../../mfc/html-help-context-sensitive-help-for-your-programs.md) y archivos de [ayuda (ayuda HTML)](../../build/reference/help-files-html-help.md) para obtener más información.

- **Impresión y vista previa de impresión**

   Genera el código para controlar los comandos de impresión, configuración de impresión y vista previa de impresión llamando a las funciones miembro de la [clase CView](../../mfc/reference/cview-class.md) de la biblioteca MFC. El asistente también agrega comandos para estas funciones al menú de la aplicación. La compatibilidad con la impresión solo está disponible para las aplicaciones que especifican la **compatibilidad con la arquitectura documento/vista** en la página [tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md) del asistente. De manera predeterminada, las aplicaciones de documento/vista son compatibles con la impresión.

- **Automatización**

   Especifica que la aplicación puede controlar objetos implementados en otra aplicación o expone la aplicación a clientes de Automation.

- **Controles ActiveX**

   Admite controles ActiveX (de forma predeterminada). Si no selecciona esta opción y posteriormente desea insertar controles ActiveX en el proyecto, debe agregar una llamada a [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) en la función miembro [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) de la aplicación.

- **MAPI (API de mensajería)**

   Especifica que la aplicación puede crear, manipular, transferir y almacenar mensajes de correo electrónico.

- **Windows Sockets**

   Admite Windows Sockets, que se pueden usar para programar aplicaciones que se comuniquen a través de redes TCP/IP.

- **Active Accessibility**

   Agrega compatibilidad con [IAccessible](/windows/win32/api/oleacc/nn-oleacc-iaccessible) a clases derivadas de [CWnd](../../mfc/reference/cwnd-class.md), que puede usar para personalizar la interfaz de usuario para una mejor interacción con los clientes de accesibilidad.

- **Manifiesto de control común**

   Habilitado de manera predeterminada. Genera un manifiesto de aplicación que habilita el archivo DLL de controles comunes incluido con Microsoft Windows XP y sistemas operativos más recientes.

   La versión 6 del archivo DLL de controles comunes no actualiza automáticamente la versión anterior de los controles comunes que se utilizan en las aplicaciones existentes. Para utilizar la versión 6 del archivo DLL de controles comunes, deberá crear un manifiesto de aplicación que indique a la aplicación que cargue el archivo DLL. Este archivo DLL de controles comunes admite también los temas de Windows XP.

   Un manifiesto de aplicación puede especificar también otros archivos DLL y otras versiones que necesite la aplicación. Para obtener más información sobre los manifiestos de aplicación, vea [aplicaciones aisladas y ensamblados en paralelo](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal) en el Windows SDK.

- **Admitir administrador de reinicio**

   Agrega compatibilidad con el [Administrador](/windows/win32/RstMgr/using-restart-manager)de reinicio de Windows. En este vídeo se muestra cómo usar el administrador de reinicio desde MFC: [Cómo: Use el nuevo administrador](/previous-versions/visualstudio/visual-studio-2010/dd831853(v%3dvs.100))de reinicio.

- **Paneles de marco avanzados**

   |Opción|DESCRIPCIÓN|
   |------------|-----------------|
   |**Panel acoplable del explorador**|Crea un panel acoplable similar al **Explorador de soluciones** de Visual Studio a la izquierda de la ventana de marco principal.|
   |**Fotograma de acoplamiento de salida**|Crea un panel acoplable similar al panel de **resultados** de Visual Studio que se encuentra en la ventana de marco principal.|
   |**Panel acoplable de propiedades**|Crea un panel acoplable similar al panel de **propiedades** de Visual Studio a la derecha de la ventana de marco principal.|
   |**Panel de navegación**|Crea un panel acoplable similar a la barra de navegación de Outlook a la izquierda de la ventana del marco principal.|
   |**Barra de título**|Crea una barra de título similar a la de Office sobre la ventana del marco principal.|

- **Número de archivos en la lista de archivos recientes**

   Especifica el número de archivos que van a aparecer en la lista de archivos utilizados recientemente. El número predeterminado es 4.

## <a name="see-also"></a>Vea también

[Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)
