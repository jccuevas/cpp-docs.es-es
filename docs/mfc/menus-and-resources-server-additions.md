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
ms.openlocfilehash: c1dfd059572c433e8fd7ccaf6e5c48e880f59cad
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445186"
---
# <a name="menus-and-resources-server-additions"></a>Menús y recursos: Adiciones de servidor

En este artículo se explican los cambios que se deben realizar en los menús y otros recursos de una aplicación de servidor de edición visual (componente). Una aplicación de servidor requiere muchas adiciones a la estructura de menú y a otros recursos, ya que se puede iniciar en uno de estos tres modos: independiente, incrustado o implementado. Tal y como se describe en el artículo de [menús y recursos (OLE)](../mfc/menus-and-resources-ole.md) , hay un máximo de cuatro conjuntos de menús. Los cuatro se usan para una aplicación de servidor completo MDI, mientras que solo se usan tres para un miniservidor. El Asistente para aplicaciones creará el diseño de menú necesario para el tipo de servidor que desee. Puede que sea necesario realizar alguna personalización.

Si no usa el Asistente para aplicaciones, puede que desee consultar HIERSVR. RC, el script de recursos para la aplicación de ejemplo de MFC [HIERSVR](../overview/visual-cpp-samples.md), para ver cómo se implementan estos cambios.

Los temas que se tratan en este artículo son:

- [Adiciones del menú servidor](#_core_server_menu_additions)

- [Adiciones de tabla de aceleradores](#_core_server_application_accelerator_table_additions)

- [Adiciones de tabla de cadenas](../mfc/menus-and-resources-container-additions.md)

- [Adiciones de miniservidor](#_core_mini.2d.server_additions)

##  <a name="_core_server_menu_additions"></a>Adiciones del menú servidor

Las aplicaciones de servidor (componente) deben tener recursos de menú agregados para admitir la edición visual OLE. No es necesario cambiar los menús que se usan cuando la aplicación se ejecuta en modo independiente, pero debe agregar dos nuevos recursos de menú antes de compilar la aplicación: uno para admitir la activación en contexto y otro para admitir que el servidor esté totalmente abierto. Ambos recursos de menú se usan en aplicaciones completas y de miniservidor.

- Para admitir la activación en contexto, debe crear un recurso de menú que sea muy similar al recurso de menú que se usa cuando se ejecuta en modo independiente. La diferencia en este menú es que faltan los elementos de archivo y ventana (y los demás elementos de menú que se ocupan de la aplicación, y no los datos). La aplicación contenedora proporcionará estos elementos de menú. Para obtener más información sobre y un ejemplo de, esta técnica de combinación de menús, vea el artículo [menús y recursos: combinación de menús](../mfc/menus-and-resources-menu-merging.md).

- Para admitir la activación totalmente abierta, debe crear un recurso de menú prácticamente idéntico al recurso de menú que se usa cuando se ejecuta en modo independiente. La única modificación de este recurso de menú es que algunos elementos se han modificado para reflejar el hecho de que el servidor está funcionando en un elemento incrustado en un documento compuesto.

Además de los cambios que se muestran en este artículo, el archivo de recursos debe incluir AFXOLESV. RC, que es necesario para la implementación de biblioteca MFC. Este archivo se encuentra en el subdirectorio MFC\Include

##  <a name="_core_server_application_accelerator_table_additions"></a>Adiciones de tabla del acelerador de aplicaciones de servidor

Se deben agregar dos nuevos recursos de tabla de aceleradores a las aplicaciones de servidor; se corresponden directamente con los nuevos recursos de menú descritos anteriormente. La primera tabla de aceleradores se utiliza cuando la aplicación de servidor se activa en su lugar. Consta de todas las entradas de la tabla de aceleradores de la vista, excepto las vinculadas a los menús archivo y ventana.

La segunda tabla es casi una copia exacta de la tabla de aceleradores de la vista. Cualquier diferencia de cambios en paralelo realizados en el menú totalmente abierto mencionado en [adiciones del menú servidor](#_core_server_menu_additions).

Para obtener un ejemplo de estos cambios en la tabla de aceleradores, compare las tablas de acelerador IDR_HIERSVRTYPE_SRVR_IP y IDR_HIERSVRTYPE_SRVR_EMB con IDR_MAINFRAME en HIERSVR. Archivo RC incluido en el ejemplo de OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md). Los aceleradores de archivos y ventanas no se encuentran en la tabla en contexto y las copias exactas de ellos se encuentran en la tabla incrustada.

##  <a name="_core_string_table_additions_for_server_applications"></a>Adiciones de tabla de cadenas para aplicaciones de servidor

Solo es necesaria una adición de tabla de cadenas en una aplicación de servidor, una cadena para indicar que se produjo un error en la inicialización de OLE. Por ejemplo, esta es la entrada de tabla de cadena que genera el Asistente para aplicaciones:

|id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Error de inicialización de OLE. Asegúrese de que la versión de las bibliotecas OLE es la correcta.|

##  <a name="_core_mini.2d.server_additions"></a>Adiciones de miniservidor

Se aplican las mismas adiciones para miniservers que las mencionadas anteriormente para servidores completos. Dado que un miniservidor no se puede ejecutar en modo independiente, su menú principal es mucho menor. El menú principal creado por el Asistente para aplicaciones solo tiene un menú Archivo, que contiene solo los elementos Exit y about. Los menús y aceleradores integrados y en contexto para miniservers son los mismos que para los servidores completos.

## <a name="see-also"></a>Consulte también

[Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md)
