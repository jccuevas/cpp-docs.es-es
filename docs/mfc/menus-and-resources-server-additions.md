---
title: "Men&#250;s y recursos: Adiciones de servidor | Microsoft Docs"
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
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tablas de aceleradores [C++], aplicaciones de servidor"
  - "IDP_OLE_INIT_FAILED (macro)"
  - "error de inicialización OLE"
  - "aplicaciones de servidor OLE, menús y recursos"
  - "servidor de edición visual OLE"
  - "recursos [MFC], aplicaciones de servidor"
  - "aplicaciones de servidor, tablas de aceleradores"
  - "aplicaciones de servidor, menús y recursos OLE"
  - "servidores, adiciones de menú"
  - "edición de cadenas, aplicaciones de edición visual"
  - "tablas de cadenas, aplicaciones de edición visual"
  - "edición visual, menús y recursos de la aplicación"
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Men&#250;s y recursos: Adiciones de servidor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica los cambios que deben realizarse a los menús y otros recursos en una aplicación visual de servidor de edición \(componente\).  Una aplicación de servidor requiere muchas adiciones a la estructura de menú y otros recursos porque puede iniciarse en uno de estos tres modos: compatibilidad único, incrustado, o en contexto.  Como se describe en el artículo de [Menús y recursos \(OLE\)](../mfc/menus-and-resources-ole.md) , hay un máximo de cuatro conjuntos de menús.  Los cuatro se utilizan para una aplicación de completo\- Servidor MDI, mientras que en tres se utilizan para un miniserver.  El asistente para aplicaciones creará el diseño del menú necesario para el tipo de servidor que desee.  Alguna personalización puede ser necesaria.  
  
 Si no utiliza el asistente para aplicaciones, puede que desee examinar HIERSVR.RC, el script de recursos para la aplicación de ejemplo [HIERSVR](../top/visual-cpp-samples.md)MFC, para ver cómo se implementan estos cambios.  
  
 Temas cubiertos en incluyen de caso:  
  
-   [Adiciones de menú del Servidor](#_core_server_menu_additions)  
  
-   [Adiciones de la tabla de aceleradores](#_core_server_application_accelerator_table_additions)  
  
-   [Adiciones de la tabla de cadenas](../mfc/menus-and-resources-container-additions.md)  
  
-   [Adiciones de Miniserver](#_core_mini.2d.server_additions)  
  
##  <a name="_core_server_menu_additions"></a> Adiciones de menú del Servidor  
 Las aplicaciones de Servidor \(componente\) deben tener recursos de menú agregados para admitir la edición visual OLE.  Los menús utilizados cuando la aplicación se ejecuta en modo independiente no tienen que cambiar, pero se deben agregar a dos nuevos recursos de menú antes de compilar la aplicación: uno para admitir la activación en contexto y uno que admite el servidor que es totalmente abiertos.  Aplicaciones completas utilizan a los recursos de menú y el miniserver.  
  
-   Para admitir la activación de contexto, debe crear un recurso de menú que es muy similar al recurso de menú utilizado cuando se ejecuta en modo independiente.  La diferencia en este menú es que faltan los elementos del archivo y la ventana \(y los demás elementos de menú que se ocupan de la aplicación, y no los datos\).  La aplicación contenedora proporcionará estos elementos de menú.  Para obtener más información sobre, y un ejemplo de, esta técnica de menú\- combinación, vea el artículo [Menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md).  
  
-   Para admitir la activación totalmente abiertos, debe crear un recurso de menú casi idéntico al recurso de menú utilizado cuando se ejecuta en modo independiente.  La única modificación a este recurso de menú es que algunos elementos se repetirán para reflejar el hecho de que el servidor está trabajando en un elemento incrustado en un documento compuesto.  
  
 Además de los cambios enumerados en este caso, el archivo de recursos debe incluir AFXOLESV.RC, necesaria para la implementación de la biblioteca Microsoft Foundation Class.  Este archivo se encuentra en el subdirectorio de MFC\\Include.  
  
##  <a name="_core_server_application_accelerator_table_additions"></a> Adiciones de la tabla de aceleradores de la aplicación de servidor  
 Dos nuevos recursos de la tabla de aceleradores deben agregarse a las aplicaciones de servidor; corresponden directamente a los nuevos recursos de menú descritos previamente.  Se utiliza la primera tabla de aceleradores cuando la aplicación de servidor se provoca en contexto.  Consta de todas las entradas de la tabla de aceleradores de vista salvo los atada al archivo y a los menús Ventana.  
  
 La segunda tabla es casi una copia exacta de la tabla de aceleradores de la vista.  Cualquier cambio paralelos de las diferencias realizados en el menú totalmente abiertos mencionado en [Adiciones de menú del Servidor](#_core_server_menu_additions).  
  
 Para obtener un ejemplo de estos cambios de la tabla de aceleradores, compare las tablas de aceleradores de **IDR\_HIERSVRTYPE\_SRVR\_IP** y de **IDR\_HIERSVRTYPE\_SRVR\_EMB** con **IDR\_MAINFRAME** en el archivo de HIERSVR.RC incluido en el ejemplo OLE [HIERSVR](../top/visual-cpp-samples.md)MFC.  Los aceleradores de archivo y la ventana faltan de la tabla en contexto y exigen copias de ellas están en la tabla incrustada.  
  
##  <a name="_core_string_table_additions_for_server_applications"></a> Tabla de cadenas Adiciones para aplicaciones de servidor  
 Sólo un resumen de la tabla de cadenas es necesaria en una aplicación de servidor \(una cadena para indicar que se produjo un error en la inicialización OLE.  Como ejemplo, ésta es la entrada de la tabla de cadenas que el asistente para aplicaciones genera:  
  
|ID|String|  
|--------|------------|  
|**IDP\_OLE\_INIT\_FAILED**|Error de inicialización OLE.  Asegúrese de que la versión de las bibliotecas OLE es la correcta.|  
  
##  <a name="_core_mini.2d.server_additions"></a> Adiciones de Miniserver  
 Las mismas adiciones solicitan miniservers como las enumeradas anteriormente para los completo\- Servidores.  Dado que un miniserver no se puede ejecutar en modo independiente, el menú principal es mucho menor.  El menú principal creado por el asistente para aplicaciones solo tiene un menú archivo, ya que sólo contienen la salida y el Acerca de los elementos.  Los menús incrustados y en contexto y los aceleradores para los miniservers son los mismos que los de los completo\- Servidores.  
  
## Vea también  
 [Menús y recursos \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [Menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md)