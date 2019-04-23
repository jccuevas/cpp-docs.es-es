---
title: 'Menús y recursos: Adiciones de servidor'
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
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
ms.openlocfilehash: 85c7b6059a868e93c6c6a7ebbd7b08dac3233612
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767208"
---
# <a name="menus-and-resources-server-additions"></a>Menús y recursos: Adiciones de servidor

En este artículo se explica los cambios que deben realizarse en los menús y otros recursos en una aplicación de servidor (componente) de edición visual. Una aplicación de servidor requiere muchas adiciones a la estructura de menús y otros recursos, porque se puede iniciar en uno de tres modos: independiente, incrustado, o en su lugar. Como se describe en el [menús y recursos (OLE)](../mfc/menus-and-resources-ole.md) del artículo, hay un máximo de cuatro conjuntos de menús. Los cuatro se usan para una aplicación de servidor completo MDI, mientras que sólo se utilizan tres para un miniservidor. El Asistente para aplicaciones creará el diseño de menú necesarios para el tipo de servidor que desee. Alguna personalización puede ser necesario.

Si no usa al Asistente para aplicaciones, puede mirar HIERSVR. RC, el script de recursos para la aplicación de ejemplo MFC [HIERSVR](../overview/visual-cpp-samples.md), para ver cómo se implementan estos cambios.

Los temas tratados en este artículo incluyen:

- [Adiciones de menú del servidor](#_core_server_menu_additions)

- [Agregar tablas de aceleradores](#_core_server_application_accelerator_table_additions)

- [Agregar tablas de cadenas](../mfc/menus-and-resources-container-additions.md)

- [Adiciones de miniservidor](#_core_mini.2d.server_additions)

##  <a name="_core_server_menu_additions"></a> Adiciones de menú del servidor

Las aplicaciones de servidor (componente) deben tener los recursos de menú agregados para admitir la edición visual OLE. No es necesario que los menús que se utilizan cuando la aplicación se ejecuta en modo independiente se puede cambiar, pero debe agregar dos nuevos recursos de menú antes de compilar la aplicación: uno para admitir la activación en contexto y para admitir el servidor que esté completamente abierta. Las aplicaciones completo y miniservidor usan los recursos de menú.

- Para admitir la activación en contexto, debe crear un recurso de menú que es muy similar para el recurso de menú que se utiliza cuando se ejecuta en modo independiente. La diferencia en este menú es que faltan los elementos de archivo y ventana (y otros elementos de menú que se encargan de la aplicación y no los datos). La aplicación contenedora proporcionará estos elementos de menú. Para obtener más información sobre y un ejemplo de esta técnica de combinación de menús, vea el artículo [menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md).

- Para admitir la activación totalmente abierta, debe crear un recurso de menú casi idéntico para el recurso de menú que se utiliza cuando se ejecuta en modo independiente. La única modificación a este recurso de menú es que algunos elementos se modifican para reflejar el hecho de que el servidor está funcionando en un elemento incrustado en un documento compuesto.

Además de los cambios mostrados en este artículo, el archivo de recursos debe incluir AFXOLESV. RC, que es necesario para la implementación de la biblioteca Microsoft Foundation Class. Este archivo se encuentra en el subdirectorio MFC\Include.

##  <a name="_core_server_application_accelerator_table_additions"></a> Acelerador de la tabla incorporaciones de aplicaciones de servidor

Se deben agregar dos nuevos recursos de tabla de aceleradores a aplicaciones de servidor; se corresponden directamente con los nuevos recursos de menú que se ha descrito anteriormente. Cuando se activa la aplicación de servidor en su lugar, se usa la primera tabla de aceleradores. Consta de todas las entradas de tabla de aceleradores de la vista, excepto las que están asociadas a la ventana y el archivo de menús.

La segunda tabla es casi una copia exacta de la tabla de aceleradores de la vista. Las diferencias en paralelo los cambios realizados en el menú completamente abierto mencionado en [adiciones de menú del servidor](#_core_server_menu_additions).

Para obtener un ejemplo de estos cambios de la tabla de aceleradores, compare las tablas de aceleradores IDR_HIERSVRTYPE_SRVR_IP y IDR_HIERSVRTYPE_SRVR_EMB con IDR_MAINFRAME en el archivo HIERSVR. Archivo RC incluido en el ejemplo OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md). Faltan los aceleradores de archivo y la ventana de la tabla local y son copias exactas de ellas en la tabla insertada.

##  <a name="_core_string_table_additions_for_server_applications"></a> Agregar tablas de cadenas para las aplicaciones de servidor

Adición de la tabla de solo una cadena es necesaria en una aplicación de servidor: una cadena para indicar el error de inicialización OLE. Por ejemplo, aquí es la entrada de tabla de cadenas que genera el Asistente para aplicaciones:

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Error de inicialización OLE. Asegúrese de que las bibliotecas OLE son la versión correcta.|

##  <a name="_core_mini.2d.server_additions"></a> Adiciones de miniservidor

Se aplican las mismas adiciones miniservidores como los mencionados anteriormente para servidores completos. Dado un miniservidor no se puede ejecutar en modo independiente, el menú principal es mucho menor. El menú principal creado por el Asistente de aplicación sólo tiene un menú archivo, que contiene solo los elementos de salida y aproximadamente. Menús en contexto e incrustados y aceleradores para miniservidores son los mismos que los servidores completos.

## <a name="see-also"></a>Vea también

[Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md)
