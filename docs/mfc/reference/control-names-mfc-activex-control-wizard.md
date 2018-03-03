---
title: Nombres del control, Asistente para controles ActiveX MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.ctl.names
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f3444ec69ea96ee89ed7a0965f3575fc79e3b9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="control-names-mfc-activex-control-wizard"></a>Nombres del control, Asistente para controles ActiveX MFC
Especifique los nombres de la clase de control y la clase de página de propiedades, los nombres de tipo y escriba los identificadores para el control. Con la excepción de **nombre corto**, todos los demás campos se pueden editar por separado. Si cambia el texto para **nombre corto**, el cambio se reflejará en los nombres de todos los demás campos en esta página. Este comportamiento de nomenclatura está diseñado para que todos los nombres fácilmente identificables automáticamente a medida que desarrolla el control.  
  
 **Nombre corto**  
 Proporcione un nombre abreviado para el control. De forma predeterminada, este nombre se basa en el nombre del proyecto que proporcionó en el **nuevo proyecto** cuadro de diálogo. El nombre que proporcione determina los nombres de clase, los nombres de tipo y los identificadores de tipo, a menos que cambie estos campos individualmente.  
  
 **Nombre de la clase de control**  
 De forma predeterminada, el nombre de la clase de control se basa en el nombre corto, con `C` como prefijo y `Ctrl` como sufijo. Por ejemplo, si el control Value de corto nombre es `Price`, el nombre de clase de control es `CPriceCtrl`.  
  
 **Archivo .h de control**  
 De forma predeterminada, el nombre del archivo de encabezado se basa en el nombre corto, con `Ctrl` como sufijo y `.h` como la extensión de archivo. Por ejemplo, si el control Value de corto nombre es `Price`, el nombre de archivo de encabezado es `PriceCtrl.h`. El nombre de este campo debe coincidir con el nombre de clase del control.  
  
 **Archivo .cpp del control**  
 De forma predeterminada, el nombre del archivo de encabezado se basa en el nombre corto, con `Ctrl` como sufijo y `.cpp` como la extensión de archivo. Por ejemplo, si el control Value de corto nombre es `Price`, el nombre de archivo de encabezado es `PriceCtrl.cpp`. El nombre de este campo debe coincidir con el nombre del encabezado.  
  
 **Nombre de tipo de control**  
 De forma predeterminada, el nombre del tipo de control se basa en el nombre corto, seguido de `Control`. Por ejemplo, si el control Value de corto nombre es `Price`, el nombre de tipo de clase de control es `Price Control`. Si cambia el valor de este campo, asegúrese de que el nombre indica una herencia.  
  
 **Id. de tipo de control**  
 Establece el identificador de tipo de control de la clase de control. El control escribe esta cadena en el registro cuando se agrega a un proyecto. Aplicaciones de contenedor usan esta cadena para crear una instancia del control.  
  
 De forma predeterminada, el identificador de tipo de control se basa en el nombre del proyecto, que indica en la **nuevo proyecto** cuadro de diálogo y el nombre corto. Este nombre debe coincidir con el nombre de tipo.  
  
 De forma predeterminada, el identificador de tipo de control aparece como sigue:  
  
 *ProjectName.ShortName*Ctrl.1  
  
 Si cambia el nombre corto en este cuadro de diálogo, el identificador de tipo de control aparece como sigue:  
  
 *ProjectName.NewShortName*Ctrl.1  
  
 **Nombre de clase de página de propiedades**  
 De forma predeterminada, el nombre de la clase de página de propiedades se basa en el nombre corto, con `C` como prefijo y `PropPage` como sufijo. Por ejemplo, si el control Value de corto nombre es `Price`, es el nombre de clase de la página de propiedades `CPricePropPage`. Este nombre debe coincidir con el nombre de clase de control, le anexado `PropPage`.  
  
 **Archivo .h de página de propiedades**  
 De forma predeterminada, el nombre del archivo de encabezado de página de propiedades se basa en el nombre corto, con como un `PropPage` como sufijo y `.h` como la extensión de archivo. Por ejemplo, si el control Value de corto nombre es `Price`, es el nombre de archivo de encabezado de página de propiedades `PricePropPage.h`. Este nombre debe coincidir con el nombre de clase.  
  
 **Archivo .cpp de página de propiedades**  
 De forma predeterminada, el nombre del archivo de implementación de la página de propiedades se basa en el nombre corto, con como un `PropPage` como sufijo y `.cpp` como la extensión de archivo. Por ejemplo, si el control Value de corto nombre es `Price`, es el nombre de archivo de encabezado de página de propiedades `PricePropPage.cpp`. Este nombre debe coincidir con el nombre de archivo de encabezado.  
  
 **Nombre de tipo de página de propiedades**  
 De forma predeterminada, el nombre de tipo de página de propiedades se basa en el nombre corto, seguido de `Property Page`. Por ejemplo, si el control Value de corto nombre es `Price`, es el nombre del tipo de página de propiedades `Price Property Page`. Si cambia el valor de este campo, asegúrese de que el nombre indica la clase de control.  
  
 **Id. de tipo de página de propiedades**  
 Establece el identificador de la clase de página de propiedades. El control escribe esta cadena en el registro cuando se aplica a un proyecto. Una aplicación de contenedor usa esta cadena para crear una instancia de la página de propiedades del control.  
  
 De forma predeterminada, el identificador de tipo de página de propiedades se basa en el nombre del proyecto, que indica en la **nuevo proyecto** cuadro de diálogo y el nombre corto. Este nombre debe coincidir con el nombre de tipo.  
  
 De forma predeterminada, el identificador de tipo de página de propiedades aparece como sigue:  
  
 *ProjectName.ShortName*PropPage.1  
  
 Si cambia el nombre corto en este cuadro de diálogo, el identificador de tipo de página de propiedades aparece como sigue:  
  
 *ProjectName.NewShortName*PropPage.1  
  
## <a name="see-also"></a>Vea también  
 [Asistente para controles ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Configuración de la aplicación, Asistente para controles ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Configuración del control, Asistente para controles ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)   
 [Tipos de archivos creados para proyectos de Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)

