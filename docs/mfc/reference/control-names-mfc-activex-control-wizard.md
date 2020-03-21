---
title: Nombres del control, Asistente para controles ActiveX MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.names
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
ms.openlocfilehash: eff7b537e7fe5c19d10cce8766557a3d1ff49342
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077504"
---
# <a name="control-names-mfc-activex-control-wizard"></a>Nombres del control, Asistente para controles ActiveX MFC

Especifique los nombres de la clase de control y la clase de página de propiedades, los nombres de tipo y los identificadores de tipo para el control. Con la excepción de **nombre corto**, todos los demás campos se pueden editar de manera independiente. Si cambia el texto de **nombre corto**, el cambio se refleja en los nombres de todos los demás campos de esta página. Este comportamiento de nomenclatura se ha diseñado para facilitarle la identificación de todos los nombres a medida que desarrolla su control.

- **Nombre corto**

   Proporcione un nombre abreviado para el control. De forma predeterminada, este nombre se basa en el nombre del proyecto que proporcionó en el cuadro de diálogo **nuevo proyecto** . El nombre que proporcione determina los nombres de clase, los nombres de tipo y los identificadores de tipo, a menos que cambie los campos de forma individual.

- **Nombre de clase de control**

   De forma predeterminada, el nombre de la clase de control se basa en el nombre corto, con `C` como prefijo y `Ctrl` como sufijo. Por ejemplo, si el nombre corto del control es `Price`, el nombre de la clase de control es `CPriceCtrl`.

- **Control. h (archivo)**

   De forma predeterminada, el nombre del archivo de encabezado se basa en el nombre corto, con `Ctrl` como sufijo y `.h` como la extensión de archivo. Por ejemplo, si el nombre corto del control es `Price`, el nombre del archivo de encabezado es `PriceCtrl.h`. El nombre de este campo debe coincidir con el nombre de clase del control.

- **Archivo. cpp de control**

   De forma predeterminada, el nombre del archivo de encabezado se basa en el nombre corto, con `Ctrl` como sufijo y `.cpp` como la extensión de archivo. Por ejemplo, si el nombre corto del control es `Price`, el nombre del archivo de encabezado es `PriceCtrl.cpp`. El nombre de este campo debe coincidir con el nombre del encabezado.

- **Nombre del tipo de control**

   De forma predeterminada, el nombre del tipo de control se basa en el nombre corto seguido de `Control`. Por ejemplo, si el nombre corto del control es `Price`, el nombre del tipo de clase de control es `Price Control`. Si cambia el valor en este campo, asegúrese de que el nombre indica una herencia.

- **IDENTIFICADOR de tipo de control**

   Establece el identificador de tipo de control de la clase de control. El control escribe esta cadena en el registro cuando se agrega a un proyecto. Las aplicaciones contenedoras usan esta cadena para crear una instancia del control.

   De forma predeterminada, el identificador del tipo de control se basa en el nombre del proyecto, que se indicó en el cuadro de diálogo **nuevo proyecto** y el nombre corto. Este nombre debe coincidir con el nombre de tipo.

   De forma predeterminada, el identificador de tipo de control aparece de la siguiente manera:

   *NombreDeProyecto. nombre_corto* Ctrl. 1

   Si cambia el nombre corto en este cuadro de diálogo, el ID. de tipo de control aparece de la manera siguiente:

   *Projectname. NewShortName* Ctrl. 1

- **PropPage (nombre de clase)**

   De forma predeterminada, el nombre de la clase de página de propiedades se basa en el nombre corto, con `C` como prefijo y `PropPage` como sufijo. Por ejemplo, si el nombre corto del control es `Price`, el nombre de clase de la página de propiedades es `CPricePropPage`. Este nombre debe coincidir con el nombre de clase del control, anexado con `PropPage`.

- **Archivo PropPage. h**

   De forma predeterminada, el nombre del archivo de encabezado de página de propiedades se basa en el nombre corto, con como `PropPage` como sufijo y `.h` como extensión de archivo. Por ejemplo, si el nombre corto del control es `Price`, el nombre del archivo de encabezado de la página de propiedades es `PricePropPage.h`. Este nombre debe coincidir con el nombre de clase.

- **Archivo PropPage. cpp**

   De forma predeterminada, el nombre del archivo de implementación de la página de propiedades se basa en el nombre corto, con como `PropPage` como sufijo y `.cpp` como extensión de archivo. Por ejemplo, si el nombre corto del control es `Price`, el nombre del archivo de encabezado de la página de propiedades es `PricePropPage.cpp`. Este nombre debe coincidir con el nombre del archivo de encabezado.

- **Nombre del tipo PropPage**

   De forma predeterminada, el nombre del tipo de página de propiedades se basa en el nombre corto seguido de `Property Page`. Por ejemplo, si el nombre corto del control es `Price`, el nombre del tipo de página de propiedades es `Price Property Page`. Si cambia el valor en este campo, asegúrese de que el nombre indica la clase del control.

- **IDENTIFICADOR de tipo PropPage**

   Establece el identificador de la clase de página de propiedades. El control escribe esta cadena en el registro cuando se aplica a un proyecto. Una aplicación contenedora utiliza esta cadena para crear una instancia de la página de propiedades del control.

   De forma predeterminada, el identificador de tipo de la página de propiedades se basa en el nombre del proyecto, que se indicó en el cuadro de diálogo **nuevo proyecto** y el nombre corto. Este nombre debe coincidir con el nombre de tipo.

   De forma predeterminada, el identificador de tipo de la página de propiedades aparece de la siguiente manera:

   *NombreDeProyecto. nombre_corto* PropPage 1

   Si cambia el nombre corto en este cuadro de diálogo, el ID. de tipo de página de propiedades aparece de la siguiente manera:

   *Projectname. NewShortName* PropPage 1

## <a name="see-also"></a>Consulte también

[Asistente para controles ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Configuración de la aplicación, Asistente para controles ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Configuración del control, Asistente para controles ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)<br/>
[Tipos de archivos creados para proyectos de C++ de Visual Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md)
