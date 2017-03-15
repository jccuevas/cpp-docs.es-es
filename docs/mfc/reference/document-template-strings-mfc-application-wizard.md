---
title: "Cadenas de plantillas de documentos, Asistente para aplicaciones MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.exe.doctemp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para aplicaciones MFC, cadenas de plantillas de documentos"
ms.assetid: 8109f662-3182-4682-977a-2503321c678a
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Cadenas de plantillas de documentos, Asistente para aplicaciones MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En esta página del Asistente para aplicaciones MFC puede proporcionar o refinar las siguientes opciones como ayuda para la administración y búsqueda de documentos.  Las cadenas de plantillas de documentos están disponibles para las aplicaciones que incluyan **Compatibilidad con la arquitectura documento\/vista** en el [Tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md).  No están disponibles para cuadros de diálogo.  Como la mayoría de las cadenas de plantillas de documentos están visibles y las utilizan los usuarios de la aplicación, están traducidas al **Idioma de los recursos** indicado en la página **Tipo de aplicación** del asistente.  
  
 **Cadenas no traducidas**  
 Se aplica a las aplicaciones que crean documentos de usuario.  Los usuarios podrán abrir, imprimir y guardar los documentos más fácilmente si se proporcionan una extensión de archivo y un identificador del tipo de archivo.  Estos elementos no están adaptados porque los utiliza el sistema, no el usuario.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Extensión de archivo**|Establece la extensión de archivo asociada a los documentos que guarda el usuario al utilizar la aplicación.  Por ejemplo, si el nombre del proyecto es Widget, podría asignar al archivo la extensión .wgt. Cuando escriba la extensión de archivo, no incluya el punto.<br /><br /> Si especifica una extensión de archivo, el Explorador podrá imprimir los documentos de la aplicación sin iniciarla cuando el usuario coloque el icono de documento en un icono de impresora.<br /><br /> Si no especifica una extensión, el usuario deberá especificar una extensión de archivo al guardar archivos.  El asistente no proporciona una extensión de archivo predeterminada.|  
|**Id. de tipo de archivo**|Establece la etiqueta para el tipo de documento en el Registro del sistema.|  
  
 **Cadenas traducidas**  
 Produce cadenas asociadas a la aplicación y el documento que leen y utilizan los usuarios de la aplicación, por lo que las cadenas están localizadas.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Idioma**|Indica el idioma en que se muestran las cadenas para todos los cuadros situadas bajo **Cadenas traducidas**.  Para cambiar el valor de este cuadro, seleccione el idioma apropiado en **Idioma de los recursos** en la página [Tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) del Asistente para aplicaciones MFC.|  
|**Título del marco principal**|Establece el texto que aparece en la parte superior del marco principal de la aplicación.  De manera predeterminada, es el nombre del proyecto.|  
|**Nombre del tipo de documento**|Identifica el tipo de documento bajo el que puede agruparse un documento de la aplicación.  De manera predeterminada, es el nombre del proyecto.  Cambiar el valor predeterminado no afecta a las demás opciones de este cuadro de diálogo.|  
|**Nombre de filtro**|Establece el nombre que los usuarios pueden indicar para buscar archivos de ese tipo de archivos.  Esta opción está disponible en las opciones **Tipo de archivos** y **Tipo** de los cuadros de diálogo estándar de Windows **Abrir** y **Guardar como**.  De forma predeterminada, el nombre del proyecto más Files, seguido por la extensión especificada en **Extensión de archivo**.  Por ejemplo, si el nombre del proyecto es Widget y la extensión de archivo es .wgt, el valor de **Nombre de filtro** será Widget Files \(\*.wgt\) de manera predeterminada.|  
|**Nuevo nombre corto del archivo**|Establece el nombre que aparece en el cuadro de diálogo `New` estándar de Windows, si hay más de una plantilla de documento.  Si su aplicación es un [servidor de automatización](../../mfc/automation-servers.md), se utiliza este nombre como nombre corto del objeto de automatización.  De manera predeterminada, es el nombre del proyecto.|  
|**Nombre largo del tipo de archivo**|Establece el nombre del tipo de archivo en el Registro del sistema.  Si su aplicación es un servidor de automatización, se utiliza este nombre como nombre largo del objeto de automatización.  De manera predeterminada, es el nombre del proyecto más .Document.|  
  
## Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)