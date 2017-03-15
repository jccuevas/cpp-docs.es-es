---
title: "Cadenas de plantillas de documentos, Asistente para agregar clases MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.mfc.simple.doctemp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para agregar clases MFC, cadenas de controles de documentos"
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Cadenas de plantillas de documentos, Asistente para agregar clases MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta página del asistente sólo está disponible para las clases que cumplen los siguientes criterios:  
  
-   El proyecto MFC es compatible con la arquitectura documento\/vista.  
  
-   La clase base de la nueva clase es [CFormView](../../mfc/reference/cformview-class.md).  
  
-   La casilla **Generar recursos DocTemplate** está activada en la sección **Nombres** del [Asistente para clases MFC](../../mfc/reference/mfc-add-class-wizard.md).  
  
 El asistente proporciona valores predeterminados para las siguientes opciones para ayudar en el diseño de vistas, administración y adaptación a otros idiomas de los formularios.  Debido a que la mayoría de las cadenas de plantillas de documento son visibles y son utilizadas por los usuarios del formulario, se traducen al **Idioma de los recursos** indicado en la página [Tipos de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) del Asistente para aplicaciones MFC cuando se creó el proyecto.  
  
> [!NOTE]
>  El asistente no proporciona automáticamente compatibilidad con impresión a las clases derivadas de `CFormView`.  
  
 Vea [Plantillas de documento y el proceso de creación de documentos y vistas](../../mfc/document-templates-and-the-document-view-creation-process.md) para obtener más información.  
  
## Cadenas no traducidas  
 Se aplica a las aplicaciones que crean documentos de usuario.  Los usuarios podrán abrir y guardar los documentos más fácilmente si el tipo de documento tiene una extensión de archivo y un identificador del tipo de archivo.  Estos elementos no están adaptados porque los utiliza el sistema, no el usuario.  
  
 **Extensión de archivo**  
 Establece la extensión de archivo asociada al tipo de documento para esta aplicación de formulario.  La extensión de archivo predeterminada se basa en el nombre de clase.  Por ejemplo, si la nueva clase MFC se denomina **CWidget**, de forma predeterminada la extensión de archivo será .wid.  La extensión de archivo se usa en filtros de archivos y en los cuadros de diálogo **Abrir** y **Guardar como**.  
  
 Si cambia la extensión de archivo, el cambio quedará reflejado en el cuadro **Nombre de filtro.**  
  
> [!NOTE]
>  Si cambia la extensión de archivo predeterminada, no incluya el punto.  
  
 **Id. de tipo de archivo**  
 Establece la etiqueta para el tipo de documento en el Registro del sistema.  
  
## Cadenas traducidas  
 Genera cadenas asociadas a los formularios y documentos que leen y utilizan los usuarios de la aplicación, para que puedan traducirse a otros idiomas.  
  
 **Nombre del tipo de documento**  
 Identifica el tipo de documento bajo el que puede agruparse un documento de la aplicación.  De forma predeterminada, está basado en el nombre de la clase.  Por ejemplo, si la nueva clase MFC se denomina **CWidget**, de forma predeterminada el nombre de tipo de documento será Widget.  Cambiar el valor predeterminado no afecta a las demás opciones de este cuadro de diálogo.  
  
 **Nombre de filtro**  
 Establece el nombre que los usuarios pueden indicar para buscar archivos del tipo de archivo especificado.  Esta opción está disponible en las opciones **Tipo de archivos** y **Tipo** de los cuadros de diálogo estándar de Windows **Abrir** y **Guardar como**.  De forma predeterminada, el nombre está basado en el nombre del proyecto más la palabra "Archivos", seguido de la extensión indicada en **Extensión de archivo**.  Por ejemplo, si su proyecto se denomina Widget y la extensión de archivo es .wid, el **Nombre de filtro** será Archivos Widget \(\*.wid\) de forma predeterminada.  
  
 **Nuevo nombre corto del archivo**  
 Establece el nombre que aparece en el cuadro de diálogo estándar de Windows `New`, si el proyecto tiene más de una plantilla de documento.  Si su aplicación es un [servidor de automatización](../../mfc/automation-servers.md), se utiliza este nombre como nombre corto del objeto de automatización.  De forma predeterminada, este nombre se basa en el nombre de clase.  
  
 **Nombre largo del tipo de archivo**  
 Establece el nombre del tipo de archivo en el Registro del sistema.  Si su aplicación es un servidor de automatización, se utiliza este nombre como nombre largo del objeto de automatización.  De forma predeterminada, este nombre se basa en el nombre de clase mas "Documento".  Por ejemplo, si el nombre de clase es el **Nombre largo de tipo de archivo** es Documento Widget.  
  
 **Clase de documento**  
 Indica la clase de documento del proyecto.  De forma predeterminada esta clase es la clase de documento de la aplicación principal, según se indica en la página [Revisar las clases generadas](../../mfc/reference/generated-classes-mfc-application-wizard.md) del Asistente para aplicaciones MFC.  Se puede seleccionar otra clase de documento en la lista si se agregaron más clases de documento al proyecto.  
  
## Vea también  
 [Asistente para agregar clases MFC](../../mfc/reference/mfc-add-class-wizard.md)   
 [MFC \(clase\)](../../mfc/reference/adding-an-mfc-class.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)