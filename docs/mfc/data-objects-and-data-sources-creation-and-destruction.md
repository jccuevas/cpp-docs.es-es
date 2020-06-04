---
title: 'Objetos de datos y orígenes de datos: Creación y destrucción'
ms.date: 11/04/2016
helpviewer_keywords:
- destroying data objects [MFC]
- object creation [MFC], data source objects
- data sources [MFC], and data objects
- data source objects [MFC], creating
- destruction [MFC], data sources
- data source objects [MFC], destroying
- data objects [MFC], creating
- data objects [MFC], destroying
- data sources [MFC], role
- data sources [MFC], destroying
- destruction [MFC], data objects
- data sources [MFC], creating
ms.assetid: ac216d54-3ca5-4ce7-850d-cd1f6a90d4f1
ms.openlocfilehash: 58b68ca9597fd2a03cffb2bbab327dbc72d09599
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371213"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Objetos de datos y orígenes de datos: Creación y destrucción

Como se explica en el artículo Objetos de datos y orígenes de datos [(OLE),](../mfc/data-objects-and-data-sources-ole.md)los objetos de datos y los orígenes de datos representan ambos lados de una transferencia de datos. En este artículo explica cuándo se deben crear y destruir estos objetos y orígenes para realizar a las transferencias de datos correctamente, incluidas estas acciones:

- [Creación de objetos de datos](#_core_creating_data_objects)

- [Destruir objetos de datos](#_core_destroying_data_objects)

- [Creación de orígenes de datos](#_core_creating_data_sources)

- [Destruir orígenes de datos](#_core_destroying_data_sources)

## <a name="creating-data-objects"></a><a name="_core_creating_data_objects"></a>Creación de objetos de datos

Los objetos de datos los usa la aplicación de destino, ya sea de cliente o de servidor. Un objeto de datos de la aplicación de destino es un extremo de una conexión entre la aplicación de origen y la aplicación de destino. Un objeto de datos de la aplicación de destino se usa para acceder a los datos del origen de datos e interactuar con ellos.

Existen dos situaciones comunes en las que es necesario un objeto de datos. La primera sucede al colocar datos en la aplicación con el proceso de arrastrar y colocar. La segunda sucede al elegir Pegar o Pegado especial en el menú Edición.

En el caso de arrastrar y colocar, no es necesario crear un objeto de datos. Se pasará a la función `OnDrop` un puntero a un objeto de datos existente. Este objeto de datos lo crea el marco como parte de la operación de arrastrar y colocar, y también será el encargado de destruirlo. Si otro método se encarga de pegar, esto no siempre es así. Para obtener más información, consulte [Destruir objetos](#_core_destroying_data_objects)de datos .

Si la aplicación realiza una operación de pegar o de pegado especial, debe crear un objeto `COleDataObject` y llamar a su función miembro `AttachClipboard`. De este modo, el objeto de datos se asocia con los datos del Portapapeles. Después puede usar este objeto de datos en la función de pegar.

## <a name="destroying-data-objects"></a><a name="_core_destroying_data_objects"></a>Destruir objetos de datos

Si sigue el esquema descrito en Creación de [objetos](#_core_creating_data_objects)de datos , la destrucción de objetos de datos es un aspecto trivial de las transferencias de datos. MFC destruirá el objeto de datos que se creó con la función para pegar cuando se vuelva a iniciar la función para pegar.

Si sigue otro método para controlar las operaciones de pegado, asegúrese de que se destruya el objeto de datos una vez completada la operación. Hasta que se destruya el objeto de datos, ninguna aplicación podrá copiar correctamente los datos en el Portapapeles.

## <a name="creating-data-sources"></a><a name="_core_creating_data_sources"></a>Creación de orígenes de datos

Los orígenes de datos los usa el origen de la transferencia de datos, que puede ser el lado del cliente o el lado del servidor de la transferencia de datos. Un origen de datos de la aplicación de origen es un extremo de una conexión entre la aplicación de origen y la aplicación de destino. Un objeto de datos de la aplicación de destino se usa para interactuar con los datos del origen de datos.

Los orígenes de datos se crean cuando una aplicación tiene que copiar datos en el Portapapeles. Un escenario habitual sería el siguiente:

1. El usuario selecciona algunos datos.

1. El usuario elige **Copiar** (o **Cortar)** en el menú **Edición** o comienza una operación de arrastrar y colocar.

1. Según el diseño del programa, la aplicación crea un objeto `COleDataSource` o un objeto de una clase derivada de `COleDataSource`.

1. Los datos seleccionados se insertan en el origen de datos con una llamada a una de las funciones de los grupos `COleDataSource::CacheData` o `COleDataSource::DelayRenderData`.

1. La aplicación llama a la función miembro `SetClipboard` (o la función miembro `DoDragDrop` si se trata de una operación de arrastrar y colocar) que pertenece al objeto creado en el paso 3.

1. Si se trata de `DoDragDrop` una operación de **corte** o devuelve **DROPEFFECT_MOVE**, los datos seleccionados en el paso 1 se eliminan del documento.

Los ejemplos OLE de MFC [oCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md)implementan este escenario. Para cada clase derivada de `CView` de la aplicación, examine el código fuente para todas las funciones excepto `GetClipboardData` y `OnGetClipboardData`. Estas dos funciones están en las implementaciones de clase derivada `COleClientItem` o `COleServerItem`. Estos programas de ejemplo constituyen una buena muestra de cómo implementar estos conceptos.

Otra situación en la que puede que quiera crear un objeto `COleDataSource` sucede cuando modifica el comportamiento predeterminado de una operación de arrastrar y colocar. Para obtener más información, vea el artículo [Arrastrar y colocar OLE: Personalizar arrastrar y colocar.](../mfc/drag-and-drop-ole.md#customize-drag-and-drop)

## <a name="destroying-data-sources"></a><a name="_core_destroying_data_sources"></a>Destruir fuentes de datos

La aplicación responsable de los orígenes de datos debe destruirlos. En situaciones en las que se entrega el origen de datos a OLE, `pDataSrc->InternalRelease`como llamar a [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop), debe llamar . Por ejemplo:

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Si no ha entregado el origen de datos a OLE, el usuario es el responsable de destruirlo, igual que sucede con cualquier objeto habitual de C++.

Para obtener más información, vea [Arrastrar y colocar](../mfc/drag-and-drop-ole.md), [Portapapeles](../mfc/clipboard.md)y Manipulación de objetos de [datos y orígenes](../mfc/data-objects-and-data-sources-manipulation.md)de datos .

## <a name="see-also"></a>Consulte también

[Objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject (clase)](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource (clase)](../mfc/reference/coledatasource-class.md)
