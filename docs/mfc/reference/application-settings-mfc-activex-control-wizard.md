---
title: Configuración de la aplicación, Asistente para controles ActiveX MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.appset
helpviewer_keywords:
- MFC ActiveX Control Wizard, application settings
ms.assetid: 48475194-cc63-467f-8499-f142269a4c1c
ms.openlocfilehash: 3201b5882a1de4064d924fbb28ee1c575ab8ccbe
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281166"
---
# <a name="application-settings-mfc-activex-control-wizard"></a>Configuración de la aplicación, Asistente para controles ActiveX MFC

Use esta página del Asistente para controles ActiveX MFC para diseñar y agregar características básicas a un nuevo proyecto de control ActiveX MFC. Esta configuración se aplica a la aplicación en sí, pero no a las características o los elementos específicos del control.

- **Licencia en tiempo de ejecución**

   Seleccione esta opción para generar un archivo de licencia de usuario para distribuir con el control. La licencia es un archivo de texto *nombre_proyecto*.lic. Este archivo debe estar en el mismo directorio que el archivo DLL del control para permitir la creación de una instancia del control en un entorno en tiempo de diseño. Normalmente distribuirá este archivo con el control, pero los clientes no lo distribuirán.

- **Generar archivos de ayuda**

   Seleccione esta opción para generar archivos de ayuda auxiliares y configurar el proyecto para incluir ayuda del control. Un proyecto predeterminado, creado sin esta opción, solo genera un cuadro **Acerca de** que se muestra cuando el usuario hace clic con el botón derecho en el control, presiona F1 o hace clic en **Ayuda** en el contenedor del control.

   > [!NOTE]
   > La forma de presentar la ayuda depende de cómo interactúa el control con su contenedor. Si quiere incluir la ayuda con el contenedor, debe controlar los mensajes emitidos entre el control y el contenedor para mostrar la ayuda de forma adecuada.

   Al generar archivos de ayuda a través del asistente, el proyecto incluye lo siguiente:

   - El archivo .vcxproj contiene código para compilar y configurar el archivo de ayuda cuando se compile el proyecto.

   - El archivo *nombre_proyecto_pág_prop*.cpp incluye una función [SetHelpInfo](../../mfc/reference/colepropertypage-class.md#sethelpinfo) en el constructor.

   - El archivo nombre_proyecto.hpj, es el archivo de proyecto de ayuda que el compilador de ayuda usa para crear el archivo de ayuda del control ActiveX. El archivo .hpj es un archivo de texto que contiene la información sobre cómo compilar el archivo de ayuda y las rutas de acceso a los archivos adicionales (por ejemplo, mapas de bits) que incluye el archivo de ayuda.

   - El proyecto incluye el directorio HLP, que contendrá los archivos de mapa de bits de ayuda del proyecto y el archivo de temas de ayuda (*nombre_proyecto*.rtf). Este archivo de temas de ayuda contiene los temas de ayuda estándar para las propiedades, los eventos y los métodos admitidos por muchos controles ActiveX comunes. Puede editar el archivo .rtf para agregar o quitar temas de ayuda específicos.

## <a name="see-also"></a>Vea también

[Asistente para controles ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Nombres del control, Asistente para controles ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)<br/>
[Configuración del control, Asistente para controles ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)
