---
title: 'Menús y recursos: adiciones de contenedor | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
dev_langs:
- C++
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 437b80a0766a07b181a60743e79bdbaf32347de4
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930552"
---
# <a name="menus-and-resources-container-additions"></a>Menús y recursos: Adiciones de contenedor
En este artículo se describen los cambios que deben realizarse en los menús y otros recursos en una aplicación de contenedor de edición visual.  
  
 En aplicaciones de contenedor, es necesario realizar dos tipos de cambios: modificaciones a los recursos existentes para admitir la edición visual OLE y la adición de nuevos recursos para la activación en contexto. Si utiliza al Asistente para aplicaciones para crear la aplicación contenedora, estos pasos se realizará automáticamente, pero pueden requerir alguna personalización.  
  
 Si no utiliza al Asistente para aplicaciones, puede que desee consultar OCLIENT. RC, el script del recurso para la aplicación de ejemplo OCLIENT, para ver cómo se implementan estos cambios. Vea el ejemplo de MFC OLE [OCLIENT](../visual-cpp-samples.md).  
  
 Los temas tratados en este artículo son:  
  
-   [Adiciones de menú de contenedor](#_core_container_menu_additions)  
  
-   [Agregar tablas de aceleradores](#_core_container_application_accelerator_table_additions)  
  
-   [Agregar tablas de cadenas](#_core_string_table_additions_for_container_applications)  
  
##  <a name="_core_container_menu_additions"></a> Adiciones de menú de contenedor  
 Debe agregar los siguientes elementos al menú Edición:  
  
|Elemento|Propósito|  
|----------|-------------|  
|**Insertar nuevo objeto**|Abre el cuadro de diálogo Insertar objeto OLE para insertar un elemento vinculado o incrustado en el documento.|  
|**Pegar vínculo**|Pega un vínculo al elemento en el Portapapeles en el documento.|  
|**Verbo OLE**|Llama a verbo principal del elemento seleccionado. El texto de este elemento de menú cambia para reflejar el verbo principal del elemento seleccionado.|  
|**Links**|Abre el cuadro de diálogo Editar vínculos OLE para cambiar los elementos vinculados existentes.|  
  
 Además de los cambios mostrados en este artículo, el archivo de origen debe incluir AFXOLECL. RC, que es necesario para la implementación de la biblioteca Microsoft Foundation Class. La adición de menú requiere solo es insertar nuevo objeto. Se pueden agregar otros elementos, pero las mencionadas aquí son las más comunes.  
  
 Debe crear un nuevo menú de la aplicación contenedora si desea admitir la activación en contexto de elementos contenidos. Este menú está formada por el mismo menú archivo y menús emergentes que utiliza cuando los archivos están abiertos, pero tiene dos separadores entre ellos. Estos separadores se utilizan para indicar que el elemento del servidor (componente) (aplicación) debe colocar sus menús cuando se activan en su lugar. Para obtener más información sobre esta técnica de combinación de menús, consulte [menús y recursos: combinación de menús](../mfc/menus-and-resources-menu-merging.md).  
  
##  <a name="_core_container_application_accelerator_table_additions"></a> Adiciones de tabla de aceleradores de aplicaciones de contenedor  
 Los pequeños cambios en recursos de tabla de aceleradores de la aplicación contenedora son necesarios si son compatibles con la activación en contexto. El primer cambio permite al usuario que presione la tecla escape (ESC) para cancelar el modo de edición en contexto. Agregue la siguiente entrada en la tabla de aceleradores principales:  
  
|Id.|Key|Tipo|  
|--------|---------|----------|  
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|  
  
 El segundo cambio consiste en crear una nueva tabla de aceleradores que se corresponde con el recurso de menú nuevo creado para la activación en contexto. Esta tabla contiene entradas para los menús archivo y ventana además de la entrada VK_ESCAPE anterior. El ejemplo siguiente es la tabla de aceleradores creada para la activación en contexto en el ejemplo MFC [contenedor](../visual-cpp-samples.md):  
  
|Id.|Key|Tipo|  
|--------|---------|----------|  
|ID_FILE_NEW|CTRL+N|**VIRTKEY**|  
|ID_FILE_OPEN|CTRL+O|**VIRTKEY**|  
|ID_FILE_SAVE|CTRL+S|**VIRTKEY**|  
|ID_FILE_PRINT|CTRL+P|**VIRTKEY**|  
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|  
|ID_PREV_PANE|MAYÚS + VK_F6|**VIRTKEY**|  
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|  
  
##  <a name="_core_string_table_additions_for_container_applications"></a> Agregar tablas de cadenas para aplicaciones de contenedor  
 La mayoría de los cambios en las tablas de cadenas para aplicaciones contenedoras corresponde a los elementos de menú adicionales mencionados en [adiciones de menú de contenedor](#_core_container_menu_additions). Que suministran el texto mostrado en la barra de estado cuando se muestra cada elemento de menú. Por ejemplo, aquí están las entradas de tabla de cadenas que genera el Asistente para aplicaciones:  
  
|Id.|String|  
|--------|------------|  
|IDP_OLE_INIT_FAILED|Error de inicialización de OLE. Asegúrese de que las bibliotecas OLE tienen la versión correcta.|  
|IDP_FAILED_TO_CREATE|No se pudo crear el objeto. Asegúrese de que el objeto especificado en el registro del sistema.|  
  
## <a name="see-also"></a>Vea también  
 [Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)   
 [Menús y recursos: Adiciones de servidor](../mfc/menus-and-resources-server-additions.md)

