---
title: 'Menús y recursos: Adiciones de servidor'
ms.date: 11/04/2016
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
ms.openlocfilehash: 8366cd8b0376766b7914c94a24cef6598761a805
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375986"
---
# <a name="menus-and-resources-server-additions"></a>Menús y recursos: Adiciones de servidor

En este artículo se explican los cambios que deben realizarse en los menús y otros recursos en una aplicación de servidor de edición visual (componente). Una aplicación de servidor requiere muchas adiciones a la estructura de menús y otros recursos porque se puede iniciar en uno de los tres modos: independiente, incrustado o en su lugar. Como se describe en el artículo [Menús y recursos (OLE),](../mfc/menus-and-resources-ole.md) hay un máximo de cuatro conjuntos de menús. Los cuatro se utilizan para una aplicación de servidor completo MDI, mientras que solo tres se utilizan para un miniservidor. El asistente de aplicación creará el diseño de menú necesario para el tipo de servidor que desee. Es posible que sea necesaria alguna personalización.

Si no utiliza el asistente de aplicación, es posible que desee ver HIERSVR. RC, el script de recursos para la aplicación de ejemplo MFC [HIERSVR](../overview/visual-cpp-samples.md), para ver cómo se implementan estos cambios.

Los temas tratados en este artículo incluyen:

- [Adiciones de menú de servidor](#_core_server_menu_additions)

- [Adiciones de mesa de acelerador](#_core_server_application_accelerator_table_additions)

- [Adiciones a tablas de cuerdas](../mfc/menus-and-resources-container-additions.md)

- [Adiciones de Miniservidor](#_core_mini.2d.server_additions)

## <a name="server-menu-additions"></a><a name="_core_server_menu_additions"></a>Adiciones de menú de servidor

Las aplicaciones de servidor (componente) deben tener recursos de menú agregados para admitir la edición visual OLE. Los menús utilizados cuando la aplicación se ejecuta en modo independiente no tienen que cambiarse, pero debe agregar dos nuevos recursos de menú antes de compilar la aplicación: uno para admitir la activación en contexto y otro para admitir el servidor totalmente abierto. Ambos recursos de menú son utilizados por aplicaciones de servidor completo y miniservidor.

- Para admitir la activación en contexto, debe crear un recurso de menú que sea muy similar al recurso de menú utilizado cuando se ejecuta en modo independiente. La diferencia en este menú es que faltan los elementos Archivo y Ventana (y cualquier otro elemento de menú que se ocupa de la aplicación y no los datos). La aplicación contenedora proporcionará estos elementos de menú. Para obtener más información y un ejemplo de esta técnica de combinación de menús, consulte el artículo [Menús y recursos: Combinación](../mfc/menus-and-resources-menu-merging.md)de menús .

- Para admitir la activación totalmente abierta, debe crear un recurso de menú casi idéntico al recurso de menú utilizado cuando se ejecuta en modo independiente. La única modificación de este recurso de menú es que algunos elementos se vuelven a redactar para reflejar el hecho de que el servidor está operando en un elemento incrustado en un documento compuesto.

Además de los cambios enumerados en este artículo, el archivo de recursos debe incluir AFXOLESV. RC, que es necesario para la implementación de la biblioteca de clases de Microsoft Foundation. Este archivo se encuentra en el subdirectorio MFC-Include.

## <a name="server-application-accelerator-table-additions"></a><a name="_core_server_application_accelerator_table_additions"></a>Adiciones de tabla del Acelerador de aplicaciones de servidor

Se deben agregar dos nuevos recursos de tabla de aceleradores a las aplicaciones de servidor; corresponden directamente a los nuevos recursos de menú descritos anteriormente. La primera tabla de aceleradores se utiliza cuando la aplicación de servidor se activa en su lugar. Consta de todas las entradas de la tabla aceleradora de la vista, excepto las vinculadas a los menús Archivo y Ventana.

La segunda tabla es casi una copia exacta de la tabla aceleradora de la vista. Cualquier diferencia de cambios paralelos realizados en el menú totalmente abierto mencionado en [Adiciones](#_core_server_menu_additions)de menú de servidor .

Para obtener un ejemplo de estos cambios en la tabla de aceleradores, compare las tablas de aceleradores IDR_HIERSVRTYPE_SRVR_IP y IDR_HIERSVRTYPE_SRVR_EMB con IDR_MAINFRAME en HIERSVR. RC incluido en el ejemplo OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md). Los aceleradores File y Window no se encuentran en la tabla in situ y las copias exactas de ellos se encuentran en la tabla incrustada.

## <a name="string-table-additions-for-server-applications"></a><a name="_core_string_table_additions_for_server_applications"></a>Adiciones de tabla de cadenas para aplicaciones de servidor

Solo es necesaria una adición de tabla de cadenas en una aplicación de servidor: una cadena para significar que se produjo un error en la inicialización ole. Por ejemplo, aquí está la entrada de tabla de cadenas que genera el asistente de aplicación:

|id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Error en la inicialización OLE. Asegúrese de que las bibliotecas OLE son la versión correcta.|

## <a name="miniserver-additions"></a><a name="_core_mini.2d.server_additions"></a>Adiciones de Miniservidor

Las mismas adiciones se aplican a los miniservidores que los enumerados anteriormente para los servidores completos. Dado que un miniservidor no se puede ejecutar en modo independiente, su menú principal es mucho más pequeño. El menú principal creado por el asistente de aplicación solo tiene un menú Archivo, que contiene solo los elementos Salir y Acerca de. Los menús y aceleradores integrados y in situ para miniservidores son los mismos que los de los servidores completos.

## <a name="see-also"></a>Consulte también

[Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md)
