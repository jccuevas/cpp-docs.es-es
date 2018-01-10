---
title: Cadenas de plantilla, Asistente para aplicaciones MFC de documentos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.exe.doctemp
dev_langs: C++
helpviewer_keywords: MFC Application Wizard, document template strings
ms.assetid: 8109f662-3182-4682-977a-2503321c678a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d2fdabb971ab9aad06f5500b98e9d8591266c85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="document-template-strings-mfc-application-wizard"></a>Cadenas de plantillas de documentos, Asistente para aplicaciones MFC
En esta página del Asistente para aplicaciones MFC, puede proporcionar o refinar las siguientes opciones para facilitar la localización y administración de documentos. Cadenas de plantillas de documento están disponibles para las aplicaciones que incluyen **compatibilidad con la arquitectura documento/vista** en el [tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md). No están disponibles para los cuadros de diálogo. Dado que la mayoría de las cadenas de plantilla de documento son visibles y son utilizadas por los usuarios de la aplicación, las páginas están localizadas en el **idioma de recurso** indicada en el **tipo de aplicación** página del asistente.  
  
 **Cadenas no localizadas**  
 Se aplica a las aplicaciones que crean documentos de usuario. Los usuarios pueden abrir, imprimir y guardar los documentos más fácilmente si se proporciona una extensión de archivo y un identificador de tipo de archivo. Estos elementos no están localizados ya que se usan por el sistema en lugar de por el usuario.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Extensión de archivo**|Establece la extensión de archivo asociada a los documentos que el usuario se guarda cuando se usa la aplicación. Por ejemplo, si el proyecto se denomina Widget, el nombre podría la .wgt de extensión de archivo. (Cuando se especifica la extensión de archivo, no incluya el punto.)<br /><br /> Si se proporciona una extensión de archivo, el explorador puede imprimir documentos de la aplicación sin necesidad de iniciar la aplicación cuando el usuario coloca el icono del documento en un icono de impresora.<br /><br /> Si no especifica una extensión, un usuario debe especificar una extensión de archivo al guardar los archivos. El asistente no proporciona una extensión de archivo predeterminada.|  
|**Id. de tipo de archivo**|Establece la etiqueta para el tipo de documento en el registro del sistema.|  
  
 **Cadenas localizadas**  
 Genera cadenas asociadas a la aplicación y el documento que leen y utilizan los usuarios de la aplicación, por lo que las cadenas están localizadas.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Idioma**|Indica el idioma en el que se muestran las cadenas para todos los cuadros en **cadenas traducidas**. Para cambiar el valor de este cuadro, seleccione el idioma apropiado en **idioma de recurso** en el [tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) página del Asistente para aplicaciones MFC.|  
|**Título del marco principal**|Establece el texto que aparece en la parte superior del marco de la aplicación principal. De forma predeterminada, el nombre del proyecto.|  
|**Nombre del tipo de documento**|Identifica el tipo de documento en la que se puede agrupar un documento de la aplicación. De forma predeterminada, el nombre del proyecto. Cambiar el valor predeterminado, no cambie ninguna otra opción en este cuadro de diálogo.|  
|**Nombre de filtro**|Establece el nombre que los usuarios pueden indicar para buscar archivos de su tipo de archivo. Esta opción está disponible desde el **archivos de tipo** y **Guardar como tipo** opciones en las ventanas estándares **abiertos** y **Guardar como** cuadros de diálogo. De forma predeterminada, el nombre del proyecto más archivos, seguido de la extensión proporcionada en **la extensión de archivo**. Por ejemplo, si el proyecto se denomina Widget y la extensión de archivo es .wgt, el **nombre de filtro** será Widget Files (*.wgt) de forma predeterminada.|  
|**Nuevo nombre corto del archivo**|Establece el nombre que aparece en el estándar de Windows `New` cuadro de diálogo, si hay más de una plantilla de documento. Si la aplicación es un [del servidor de automatización](../../mfc/automation-servers.md), este nombre se utiliza como el nombre corto del objeto de automatización. De forma predeterminada, el nombre del proyecto.|  
|**Nombre largo del tipo de archivo**|Establece el nombre de tipo de archivo en el registro del sistema. Si la aplicación es un servidor de automatización, este nombre se usa como el nombre largo de su objeto de automatización. De forma predeterminada, el nombre del proyecto más. Documento.|  
  
## <a name="see-also"></a>Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)

