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
ms.openlocfilehash: a082a75ef0292e190e597f29be0cdc0bd0b497ef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626240"
---
# <a name="menus-and-resources-container-additions"></a>Menús y recursos: Adiciones de contenedor

En este artículo se explican los cambios que se deben realizar en los menús y otros recursos de una aplicación contenedora de edición visual.

En las aplicaciones contenedoras, es necesario realizar dos tipos de cambios: modificaciones en los recursos existentes para admitir la edición visual OLE y la adición de nuevos recursos utilizados para la activación en contexto. Si usa el Asistente para aplicaciones para crear la aplicación contenedora, estos pasos se realizarán automáticamente, pero es posible que requieran alguna personalización.

Si no usa el Asistente para aplicaciones, puede que desee consultar OCLIENT. RC, el script de recursos para la aplicación de ejemplo OCLIENT, para ver cómo se implementan estos cambios. Vea el ejemplo de OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md).

Los temas que se tratan en este artículo son:

- [Adiciones del menú contenedor](#_core_container_menu_additions)

- [Adiciones de tabla de aceleradores](#_core_container_application_accelerator_table_additions)

- [Adiciones de tabla de cadenas](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>Adiciones del menú contenedor

Debe agregar los siguientes elementos al menú Edición:

|Artículo|Propósito|
|----------|-------------|
|**Insertar nuevo objeto**|Abre el cuadro de diálogo Insertar objeto OLE para insertar un elemento vinculado o incrustado en el documento.|
|**Pegar vínculo**|Pega un vínculo al elemento del portapapeles en el documento.|
|**Verbo OLE**|Llama al verbo principal del elemento seleccionado. El texto de este elemento de menú cambia para reflejar el verbo principal del elemento seleccionado.|
|**Vínculos**|Abre el cuadro de diálogo Editar vínculos de OLE para cambiar los elementos vinculados existentes.|

Además de los cambios que se muestran en este artículo, el archivo de código fuente debe incluir AFXOLECL. RC, que es necesario para la implementación de biblioteca MFC. Insertar nuevo objeto es la única adición de menús necesaria. Se pueden agregar otros elementos, pero los que se enumeran aquí son los más comunes.

Debe crear un nuevo menú para la aplicación contenedora si desea admitir la activación en contexto de los elementos contenidos. Este menú está formado por el mismo menú Archivo y los menús emergentes de la ventana que se usan cuando los archivos están abiertos, pero tiene dos separadores colocados entre ellos. Estos separadores se usan para indicar dónde debe colocar el elemento de servidor (componente) (aplicación) los menús cuando se activen. Para obtener más información sobre esta técnica de combinación de menús, vea [menús y recursos: combinación de menús](menus-and-resources-menu-merging.md).

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>Adiciones de tabla del acelerador de aplicaciones contenedoras

Los pequeños cambios en los recursos de tabla de aceleradores de la aplicación de contenedor son necesarios si se admite la activación en contexto. El primer cambio permite al usuario presionar la tecla Escape (ESC) para cancelar el modo de edición en contexto. Agregue la siguiente entrada a la tabla de aceleradores principal:

|ID|Clave|Tipo|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

El segundo cambio consiste en crear una nueva tabla de aceleradores que se corresponda con el nuevo recurso de menú creado para la activación en contexto. Esta tabla contiene entradas para los menús archivo y ventana, además de la entrada VK_ESCAPE anterior. En el ejemplo siguiente se muestra la tabla de aceleradores creada para la activación en contexto en el [contenedor](../overview/visual-cpp-samples.md)de ejemplo de MFC:

|ID|Clave|Tipo|
|--------|---------|----------|
|ID_FILE_NEW|CTRL+N|**VIRTKEY**|
|ID_FILE_OPEN|CTRL+O|**VIRTKEY**|
|ID_FILE_SAVE|CTRL+S|**VIRTKEY**|
|ID_FILE_PRINT|CTRL+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|MAYÚS + VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>Adiciones de tabla de cadenas para aplicaciones de contenedor

La mayoría de los cambios en las tablas de cadenas para las aplicaciones de contenedor se corresponden con los elementos de menú adicionales mencionados en las [adiciones del menú contenedor](#_core_container_menu_additions). Proporcionan el texto que se muestra en la barra de estado cuando se muestra cada elemento de menú. Por ejemplo, estas son las entradas de tabla de cadena que genera el Asistente para aplicaciones:

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Error de inicialización de OLE. Asegúrese de que la versión de las bibliotecas OLE es la correcta.|
|IDP_FAILED_TO_CREATE|No se pudo crear el objeto. Asegúrese de que el objeto se ha escrito en el registro del sistema.|

## <a name="see-also"></a>Consulte también

[Menús y recursos (OLE)](menus-and-resources-ole.md)<br/>
[Menús y recursos: Adiciones de servidor](menus-and-resources-server-additions.md)
