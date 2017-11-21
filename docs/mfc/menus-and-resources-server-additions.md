---
title: "Menús y recursos: adiciones de servidor | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDP_OLE_INIT_FAILED
dev_langs: C++
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 65417079c3241feca9c43e058026674c6e35d18b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="menus-and-resources-server-additions"></a>Menús y recursos: Adiciones de servidor
En este artículo se describen los cambios que deben realizarse en los menús y otros recursos en una aplicación de servidor (componente) de edición visual. Una aplicación de servidor requiere agregar muchos elementos a la estructura de menús y otros recursos porque puede iniciarse en uno de los tres modos: independiente, incrustado, o en su lugar. Como se describe en el [menús y recursos (OLE)](../mfc/menus-and-resources-ole.md) artículo, hay un máximo de cuatro conjuntos de menús. Los cuatro se usan para una aplicación de servidor completo MDI, mientras que sólo se utilizan tres para un miniservidor. El Asistente para aplicaciones creará el diseño de menú necesarios para el tipo de servidor al que desea. Alguna personalización puede ser necesario.  
  
 Si no utiliza al Asistente para aplicaciones, puede que desee consultar HIERSVR. RC, el script del recurso para la aplicación de ejemplo MFC [HIERSVR](../visual-cpp-samples.md), para ver cómo se implementan estos cambios.  
  
 Los temas tratados en este artículo son:  
  
-   [Adiciones de menú de servidor](#_core_server_menu_additions)  
  
-   [Agregar tablas de aceleradores](#_core_server_application_accelerator_table_additions)  
  
-   [Agregar tablas de cadenas](../mfc/menus-and-resources-container-additions.md)  
  
-   [Adiciones de miniservidor](#_core_mini.2d.server_additions)  
  
##  <a name="_core_server_menu_additions"></a>Adiciones de menú de servidor  
 Las aplicaciones de servidor (componente) deben tener recursos de menú agregados para admitir la edición visual OLE. No es necesario puede cambiar los menús que se utilizan cuando la aplicación se ejecuta en modo independiente, pero deberá agregar dos nuevos recursos de menú antes de compilar la aplicación: uno para permitir la activación en contexto y otro para permitir que el servidor que se abra completamente. Los recursos de menú utilizados por aplicaciones de servidor completo y miniservidor.  
  
-   Para admitir la activación en contexto, debe crear un recurso de menú que es muy similar para el recurso de menú utilizado cuando se ejecuta en modo independiente. La diferencia en este menú es que faltan los elementos archivo y ventana (y otros elementos de menú que se encargan de la aplicación y no los datos). La aplicación contenedora proporcionará estos elementos de menú. Para obtener más información sobre y un ejemplo de esta técnica de combinación de menús, vea el artículo [menús y recursos: combinación de menús](../mfc/menus-and-resources-menu-merging.md).  
  
-   Para admitir la activación totalmente abierta, debe crear un recurso de menú casi idéntico para el recurso de menú utilizado cuando se ejecuta en modo independiente. La única modificación a este recurso de menú es el que se modifican algunos elementos para reflejar el hecho de que el servidor está funcionando en un elemento incrustado en un documento compuesto.  
  
 Además de los cambios mostrados en este artículo, el archivo de recursos debe incluir AFXOLESV. RC, que es necesario para la implementación de la biblioteca Microsoft Foundation Class. Este archivo está en el subdirectorio MFC\Include.  
  
##  <a name="_core_server_application_accelerator_table_additions"></a>Adiciones de tabla de aceleradores de aplicación de servidor  
 Se deben agregar dos nuevos recursos de tabla de aceleradores a las aplicaciones de servidor; corresponden directamente con los nuevos recursos de menú descritos anteriormente. Cuando se activa la aplicación de servidor en su lugar, se utiliza la primera tabla de aceleradores. Consta de todas las entradas de tabla de aceleradores de la vista excepto las asociadas a los archivos y la ventana de menús.  
  
 La segunda tabla es prácticamente una copia exacta de la tabla de aceleradores de la vista. Cualquier diferencia en paralelo los cambios realizados en el menú completamente abierto mencionado en [adiciones de menú de servidor](#_core_server_menu_additions).  
  
 Para obtener un ejemplo de estos cambios de la tabla de aceleradores, compare el **IDR_HIERSVRTYPE_SRVR_IP** y **IDR_HIERSVRTYPE_SRVR_EMB** Acelerador de tablas con **IDR_MAINFRAME** en el ejemplo HIERSVR. Archivo RC incluido en el ejemplo de MFC OLE [HIERSVR](../visual-cpp-samples.md). Faltan los aceleradores de archivo y la ventana de la tabla en contexto y son copias exactas de ellas en la tabla incrustada.  
  
##  <a name="_core_string_table_additions_for_server_applications"></a>Agregar tablas de cadenas para las aplicaciones de servidor  
 Adición de cadena solo una tabla es necesario en una aplicación de servidor: una cadena para indicar que no se pudo la inicialización de OLE. Por ejemplo, aquí es la entrada de tabla de cadenas que genera el Asistente para aplicaciones:  
  
|Id.|Cadena|  
|--------|------------|  
|**IDP_OLE_INIT_FAILED**|Error de inicialización de OLE. Asegúrese de que las bibliotecas OLE tienen la versión correcta.|  
  
##  <a name="_core_mini.2d.server_additions"></a>Adiciones de miniservidor  
 Se aplican las mismas adiciones para miniservidores como los mencionados anteriormente para servidores completos. Dado un miniservidor no se puede ejecutar en modo independiente, el menú principal es mucho menor. El menú principal creado por el Asistente para aplicaciones sólo tiene un menú archivo, que contiene solo los elementos de salida y sobre. Menús en contexto e incrustados y aceleradores para miniservidores son los mismos que los servidores completos.  
  
## <a name="see-also"></a>Vea también  
 [Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)   
 [Menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md)

