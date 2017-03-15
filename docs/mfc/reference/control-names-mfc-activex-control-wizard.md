---
title: "Nombres del control, Asistente para controles ActiveX MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.ctl.names"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para controles ActiveX MFC, nombres del control"
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Nombres del control, Asistente para controles ActiveX MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifique los nombres de la clase de control y la clase de página de propiedades, los nombres de tipo, y los identificadores de tipo del control.  Con la excepción de **Nombre corto**, puede editar los demás campos por separado.  Si cambia el texto de **Nombre corto**, este cambio se reflejará en los nombres de los demás campos de esta página.  El comportamiento de nomenclatura está diseñado para que todos los nombres sean fácilmente identificables al crear los controles.  
  
 **Nombre corto**  
 Escriba un nombre abreviado para el control.  De manera predeterminada, este nombre se basa en el nombre del proyecto que especificó en el cuadro de diálogo **Nuevo proyecto**.  El nombre que especificó determinará los nombres de las clases, los nombres de los tipos y los identificadores de tipo, a menos que los modifique individualmente.  
  
 **Nombre de la clase del control**  
 De manera predeterminada, el nombre de la clase del control se basa en el nombre corto, con el prefijo `C` y el sufijo `Ctrl`.  Por ejemplo, si el nombre corto del control es `Price`, el nombre de la clase del control será `CPriceCtrl`.  
  
 **Archivo .h del control**  
 De manera predeterminada, el nombre del archivo de encabezado se basa en el nombre corto, con el sufijo `Ctrl` y la extensión de archivo `.h`.  Por ejemplo, si el nombre corto del control es `Price`, el nombre del archivo de encabezado será `PriceCtrl.h`.  El nombre de este campo debe coincidir con el nombre de la clase del control.  
  
 **Archivo .cpp del control**  
 De manera predeterminada, el nombre del archivo de encabezado se basa en el nombre corto, con el sufijo `Ctrl` y la extensión de archivo `.cpp`.  Por ejemplo, si el nombre corto del control es `Price`, el nombre del archivo de encabezado será `PriceCtrl.cpp`.  El nombre de este campo debe coincidir con el nombre de encabezado.  
  
 **Nombre de tipo del control**  
 De manera predeterminada, el nombre de tipo del control se basa en el nombre corto, seguido de `Control`.  Por ejemplo, si el nombre corto del control es `Price`, el nombre de tipo de clase del control será `Price Control`.  Si modifica el valor de este campo, asegúrese de que el nombre indica una herencia.  
  
 **Id. de tipo del control**  
 Establece el identificador de tipo de control de la clase de control.  El control escribe esta cadena en el Registro cuando se agrega a un proyecto.  Las aplicaciones contenedoras utilizan esta cadena para crear una instancia del control.  
  
 De manera predeterminada, el identificador de tipo del control se basa en el nombre del proyecto, que especificó en el cuadro de diálogo **Nuevo proyecto**, y en el nombre corto.  Este nombre debe coincidir con el nombre de tipo.  
  
 De forma predeterminada, el identificador de tipo de control tendrá la forma siguiente:  
  
 *Nombre\_proyecto*.*Nombre\_corto*Ctrl.1  
  
 Si cambia el nombre corto en este cuadro de diálogo, el identificador de tipo de control tendrá la forma siguiente:  
  
 *Nombre\_proyecto*.*Nuevo\_nombre\_corto*Ctrl.1  
  
 **Nombre de la clase de página de propiedades**  
 De manera predeterminada, el nombre de la clase de página de propiedades se basa en el nombre corto, con el prefijo `C` y el sufijo `PropPage`.  Por ejemplo, si el nombre corto del control es `Price`, el nombre de la clase de página de propiedades será `CPricePropPage`.  Este nombre debe coincidir con el nombre de la clase del control, con el sufijo `PropPage` anexado.  
  
 **Archivo .h de la página de propiedades**  
 De manera predeterminada, el nombre del archivo de encabezado de la página de propiedades se basa en el nombre corto, con el sufijo `PropPage` y la extensión de archivo `.h`.  Por ejemplo, si el nombre corto del control es `Price`, el nombre del archivo de encabezado de la página de propiedades será `PricePropPage.h`.  Este nombre debe coincidir con el nombre de la clase.  
  
 **Archivo .cpp de la página de propiedades**  
 De manera predeterminada, el nombre del archivo de implementación de la página de propiedades se basa en el nombre corto, con el sufijo `PropPage` y la extensión de archivo `.cpp`.  Por ejemplo, si el nombre corto del control es `Price`, el nombre del archivo de encabezado de la página de propiedades será `PricePropPage.cpp`.  Este nombre debe coincidir con el nombre del archivo de encabezado.  
  
 **Nombre de tipo de la página de propiedades**  
 De manera predeterminada, el nombre de tipo de la página de propiedades se basa en el nombre corto, seguido de `Property Page`.  Por ejemplo, si el nombre corto del control es `Price`, el nombre de tipo de la página de propiedades será `Price Property Page`.  Si modifica el valor de este campo, asegúrese de que el nombre indica la clase del control.  
  
 **Id. de tipo de la página de propiedades**  
 Establece el identificador de la clase de página de propiedades.  El control escribe esta cadena en el Registro cuando se aplica a un proyecto.  Las aplicaciones contenedoras la utilizan para crear una instancia de la página de propiedades del control.  
  
 De manera predeterminada, el identificador de tipo de página de propiedades se basa en el nombre del proyecto, que especificó en el cuadro de diálogo **Nuevo proyecto**, y en el nombre corto.  Este nombre debe coincidir con el nombre de tipo.  
  
 De forma predeterminada, el identificador de tipo de página de propiedades tendrá la forma siguiente:  
  
 *Nombre\_proyecto*.*Nombre\_corto*PropPage.1  
  
 Si cambia el nombre corto en este cuadro de diálogo, el identificador de tipo de página de propiedades tendrá la forma siguiente:  
  
 *Nombre\_proyecto*.*Nuevo\_nombre\_corto*PropPage.1  
  
## Vea también  
 [Asistente para controles ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Configuración de la aplicación, Asistente para controles ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Configuración del control, Asistente para controles ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)   
 [Tipos de archivos creados para proyectos de Visual C\+\+](../../ide/file-types-created-for-visual-cpp-projects.md)