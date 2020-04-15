---
title: 'Menús y recursos: Adiciones de contenedor'
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
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
ms.openlocfilehash: c8da58316f471f7b7d26e142cc1dd1ccaa6ad8b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364794"
---
# <a name="menus-and-resources-container-additions"></a>Menús y recursos: Adiciones de contenedor

En este artículo se explican los cambios que deben realizarse en los menús y otros recursos de una aplicación contenedora de edición visual.

En las aplicaciones de contenedor, es necesario realizar dos tipos de cambios: modificaciones en los recursos existentes para admitir la edición visual OLE y la adición de nuevos recursos utilizados para la activación in situ. Si usa el asistente de aplicación para crear la aplicación contenedora, estos pasos se realizarán por usted, pero pueden requerir alguna personalización.

Si no utiliza el asistente de aplicación, es posible que desee ver OCLIENT. RC, el script de recursos para la aplicación de ejemplo OCLIENT, para ver cómo se implementan estos cambios. Vea el ejemplo OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md).

Los temas tratados en este artículo incluyen:

- [Adiciones de menú de contenedores](#_core_container_menu_additions)

- [Adiciones de mesa de acelerador](#_core_container_application_accelerator_table_additions)

- [Adiciones a tablas de cuerdas](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>Adiciones de menú de contenedores

Debe agregar los siguientes elementos al menú Editar:

|Elemento|Propósito|
|----------|-------------|
|**Insertar nuevo objeto**|Abre el cuadro de diálogo Insertar objeto OLE para insertar un elemento vinculado o incrustado en el documento.|
|**Pegar enlace**|Pega un vínculo al elemento del Portapapeles en el documento.|
|**Verbo OLE**|Llama al verbo principal del elemento seleccionado. El texto de este elemento de menú cambia para reflejar el verbo principal del elemento seleccionado.|
|**Vínculos**|Abre el cuadro de diálogo Editar vínculos OLE para cambiar los elementos vinculados existentes.|

Además de los cambios enumerados en este artículo, el archivo de origen debe incluir AFXOLECL. RC, que es necesario para la implementación de la biblioteca de clases de Microsoft Foundation. Insertar nuevo objeto es la única adición de menú necesaria. Se pueden agregar otros elementos, pero los que se enumeran aquí son los más comunes.

Debe crear un nuevo menú para la aplicación contenedora si desea admitir la activación en contexto de elementos contenidos. Este menú consta del mismo menú Archivo y los menús emergentes Ventana utilizados cuando los archivos están abiertos, pero tiene dos separadores colocados entre ellos. Estos separadores se utilizan para indicar dónde debe colocar el elemento de servidor (componente) (aplicación) cuando se activa en su lugar. Para obtener más información sobre esta técnica de combinación de [menús, consulte Menús y recursos: combinación](../mfc/menus-and-resources-menu-merging.md)de menús .

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>Adiciones de tabla del acelerador de aplicaciones de contenedor

Los pequeños cambios en los recursos de la tabla de aceleradores de una aplicación contenedora son necesarios si admite la activación en contexto. El primer cambio permite al usuario presionar la tecla de escape (ESC) para cancelar el modo de edición in situ. Agregue la siguiente entrada a la tabla de aceleradores principal:

|id|Clave|Tipo|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

El segundo cambio consiste en crear una nueva tabla de aceleradores que corresponda al nuevo recurso de menú creado para la activación in situ. Esta tabla tiene entradas para los menús Archivo y Ventana, además de la entrada de VK_ESCAPE anterior. El ejemplo siguiente es la tabla de aceleradores creada para la activación en contexto en el [contenedor](../overview/visual-cpp-samples.md)de ejemplo MFC:

|id|Clave|Tipo|
|--------|---------|----------|
|ID_FILE_NEW|CTRL+N|**VIRTKEY**|
|ID_FILE_OPEN|CTRL+O|**VIRTKEY**|
|ID_FILE_SAVE|CTRL+S|**VIRTKEY**|
|ID_FILE_PRINT|CTRL+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|MAYÚS+VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>Adiciones de tabla de cadenas para aplicaciones de contenedor

La mayoría de los cambios en las tablas de cadenas para aplicaciones contenedoras corresponden a los elementos de menú adicionales mencionados en [Adiciones](#_core_container_menu_additions)de menú contenedor . Proporcionan el texto que se muestra en la barra de estado cuando se muestra cada elemento de menú. Por ejemplo, aquí están las entradas de tabla de cadenas que genera el asistente de la aplicación:

|id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Error en la inicialización OLE. Asegúrese de que las bibliotecas OLE son la versión correcta.|
|IDP_FAILED_TO_CREATE|No se pudo crear el objeto. Asegúrese de que el objeto se introduce en el registro del sistema.|

## <a name="see-also"></a>Consulte también

[Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menús y recursos: Adiciones de servidor](../mfc/menus-and-resources-server-additions.md)
