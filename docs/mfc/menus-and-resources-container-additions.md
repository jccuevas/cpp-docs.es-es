---
title: "Men&#250;s y recursos: Adiciones de contenedor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDP_OLE_INIT_FAILED"
  - "IDP_FAILED_TO_CREATE"
  - "VK_ESCAPE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tablas de aceleradores [C++], aplicaciones de contenedor"
  - "aplicación de tabla de aceleradores [C++]"
  - "CONTAIN (tutorial)"
  - "IDP_FAILED_TO_CREATE (macro)"
  - "IDP_OLE_INIT_FAILED (macro)"
  - "Links (elemento de menú)"
  - "contenedores OLE, menús y recursos"
  - "edición visual, menús y recursos de la aplicación"
  - "VK_ESCAPE (clave)"
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Men&#250;s y recursos: Adiciones de contenedor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica los cambios que deben realizarse a los menús y otros recursos en una aplicación contenedora de edición visual.  
  
 En aplicaciones contenedoras, dos tipos de cambios deben establecer: modificaciones en los recursos existentes para admitir la edición visual\) y la adición de nuevos recursos utilizados para la activación en contexto.  Si utiliza el asistente para aplicaciones para crear la aplicación contenedora, estos pasos se hará automáticamente, pero pueden requerir alguna personalización.  
  
 Si no utiliza el asistente para aplicaciones, puede que desee examinar OCLIENT.RC, el script de recursos para la aplicación de ejemplo OCLIENT, para ver cómo se implementan estos cambios.  Vea a MFC el ejemplo OLE [OCLIENT](../top/visual-cpp-samples.md).  
  
 Temas cubiertos en incluyen de caso:  
  
-   [Adiciones de menú de contenedor](#_core_container_menu_additions)  
  
-   [Adiciones de la tabla de aceleradores](#_core_container_application_accelerator_table_additions)  
  
-   [Adiciones de la tabla de cadenas](#_core_string_table_additions_for_container_applications)  
  
##  <a name="_core_container_menu_additions"></a> Adiciones de menú de contenedor  
 Debe agregar los siguientes elementos al menú Edición:  
  
|Elemento|Objetivo|  
|--------------|--------------|  
|**Nuevo objeto INSERT**|Abra el cuadro de diálogo OLE de objeto INSERT para insertar un elemento incrustado o vinculado en el documento.|  
|**Pegar vínculo**|Pega un vínculo al elemento en el portapapeles en el documento.|  
|**Verbo OLE**|Llama al verbo primario del elemento seleccionado.  El texto de los cambios de este elemento de menú para reflejar el verbo primario del elemento seleccionado.|  
|**Vínculos**|Abra el cuadro de diálogo OLE de los vínculos de edición para cambiar los elementos existentes.|  
  
 Además de los cambios enumerados en este caso, el archivo de código fuente debe incluir AFXOLECL.RC, necesaria para la implementación de la biblioteca Microsoft Foundation Class.  El objeto New INSERT es la única agregar necesaria de menú.  Otros elementos pueden agregar, pero los mostrados aquí son el común.  
  
 Debe crear un nuevo menú para la aplicación contenedora si desea admitir la activación en contexto de elementos contenidos.  Este menú consta del mismo menú archivo y menús emergentes de ventana empleada cuando los archivos abiertos, pero tiene dos separadores colocados entre ellos.  Estos separadores se utilizan para indicar que el elemento del servidor \(componente\) \(aplicación\) debe colocar los menús cuando se activan en contexto.  Para obtener más información sobre esta técnica de menú\- combinación, vea [Menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md).  
  
##  <a name="_core_container_application_accelerator_table_additions"></a> Adiciones de la tabla de aceleradores de la aplicación contenedora  
 Pequeños cambios en los recursos de la tabla de aceleradores de aplicación contenedora son necesarios si se admiten la activación en contexto.  El primer cambio permite que el usuario presione la tecla de escape \(ESC\) para cancelar el modo de edición en contexto.  Agregue la siguiente entrada a la tabla principal de aceleradores:  
  
|ID|Key|Tipo|  
|--------|---------|----------|  
|**ID\_CANCEL\_EDIT\_CNTR**|VK\_ESCAPE|**VIRTKEY**|  
  
 El segundo cambio es crear una nueva tabla de aceleradores que corresponde al nuevo recurso de menú creado para la activación en contexto.  Esta tabla tiene las entradas del archivo y menús Ventana además de entrada de **VK\_ESCAPE** anteriormente.  El ejemplo siguiente es una tabla de aceleradores creada para la activación en contexto en el ejemplo [CONTENEDOR](../top/visual-cpp-samples.md)de MFC:  
  
|ID|Key|Tipo|  
|--------|---------|----------|  
|`ID_FILE_NEW`|CTRL\+N|**VIRTKEY**|  
|`ID_FILE_OPEN`|CTRL\+O|**VIRTKEY**|  
|**ID\_FILE\_SAVE**|CTRL\+S|**VIRTKEY**|  
|**ID\_FILE\_PRINT**|CTRL\+P|**VIRTKEY**|  
|**ID\_NEXT\_PANE**|VK\_F6|**VIRTKEY**|  
|**ID\_PREV\_PANE**|SHIFT\+VK\_F6|**VIRTKEY**|  
|**ID\_CANCEL\_EDIT\_CNTR**|VK\_ESCAPE|**VIRTKEY**|  
  
##  <a name="_core_string_table_additions_for_container_applications"></a> Tabla de cadenas Adiciones para aplicaciones contenedoras  
 La mayoría de los cambios en las tablas de cadenas para las aplicaciones contenedoras corresponden a los elementos de menú adicionales enumerados en [Adiciones de menú de contenedor](#_core_container_menu_additions).  Escriba el texto mostrado en la barra de estado cuando se muestra cada elemento de menú.  Como ejemplo, éstas son las entradas de la tabla de cadenas que el asistente para aplicaciones genera:  
  
|ID|String|  
|--------|------------|  
|**IDP\_OLE\_INIT\_FAILED**|Error de inicialización OLE.  Asegúrese de que la versión de las bibliotecas OLE es la correcta.|  
|**IDP\_FAILED\_TO\_CREATE**|No se pudo crear el objeto.  Asegúrese de que el objeto está escrito en el sistema.|  
  
## Vea también  
 [Menús y recursos \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [Menús y recursos: Adiciones de servidor](../mfc/menus-and-resources-server-additions.md)