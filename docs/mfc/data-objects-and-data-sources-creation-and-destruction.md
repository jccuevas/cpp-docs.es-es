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
ms.openlocfilehash: 8d4edc93594bf453c61e03dca7e3117aefaa6c42
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620497"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Objetos de datos y orígenes de datos: Creación y destrucción

Como se explica en el artículo [objetos de datos y orígenes de datos (OLE)](data-objects-and-data-sources-ole.md), los objetos de datos y los orígenes de datos representan ambos lados de una transferencia de datos. En este artículo explica cuándo se deben crear y destruir estos objetos y orígenes para realizar a las transferencias de datos correctamente, incluidas estas acciones:

- [Crear objetos de datos](#_core_creating_data_objects)

- [Destruir objetos de datos](#_core_destroying_data_objects)

- [Creación de orígenes de datos](#_core_creating_data_sources)

- [Destruir orígenes de datos](#_core_destroying_data_sources)

## <a name="creating-data-objects"></a><a name="_core_creating_data_objects"></a>Crear objetos de datos

Los objetos de datos los usa la aplicación de destino, ya sea de cliente o de servidor. Un objeto de datos de la aplicación de destino es un extremo de una conexión entre la aplicación de origen y la aplicación de destino. Un objeto de datos de la aplicación de destino se usa para acceder a los datos del origen de datos e interactuar con ellos.

Existen dos situaciones comunes en las que es necesario un objeto de datos. La primera sucede al colocar datos en la aplicación con el proceso de arrastrar y colocar. La segunda sucede al elegir Pegar o Pegado especial en el menú Edición.

En el caso de arrastrar y colocar, no es necesario crear un objeto de datos. Se pasará a la función `OnDrop` un puntero a un objeto de datos existente. Este objeto de datos lo crea el marco como parte de la operación de arrastrar y colocar, y también será el encargado de destruirlo. Si otro método se encarga de pegar, esto no siempre es así. Para obtener más información, vea [destruir objetos de datos](#_core_destroying_data_objects).

Si la aplicación realiza una operación de pegar o de pegado especial, debe crear un objeto `COleDataObject` y llamar a su función miembro `AttachClipboard`. De este modo, el objeto de datos se asocia con los datos del Portapapeles. Después puede usar este objeto de datos en la función de pegar.

## <a name="destroying-data-objects"></a><a name="_core_destroying_data_objects"></a>Destruir objetos de datos

Si sigue el esquema descrito en [creación de objetos de datos](#_core_creating_data_objects), destruir objetos de datos es un aspecto trivial de las transferencias de datos. MFC destruirá el objeto de datos que se creó con la función para pegar cuando se vuelva a iniciar la función para pegar.

Si sigue otro método para controlar las operaciones de pegado, asegúrese de que se destruya el objeto de datos una vez completada la operación. Hasta que se destruya el objeto de datos, ninguna aplicación podrá copiar correctamente los datos en el Portapapeles.

## <a name="creating-data-sources"></a><a name="_core_creating_data_sources"></a>Crear orígenes de datos

Los orígenes de datos los usa el origen de la transferencia de datos, que puede ser el lado del cliente o el lado del servidor de la transferencia de datos. Un origen de datos de la aplicación de origen es un extremo de una conexión entre la aplicación de origen y la aplicación de destino. Un objeto de datos de la aplicación de destino se usa para interactuar con los datos del origen de datos.

Los orígenes de datos se crean cuando una aplicación tiene que copiar datos en el Portapapeles. Un escenario habitual sería el siguiente:

1. El usuario selecciona algunos datos.

1. El usuario elige **copiar** (o **cortar**) en el menú **Editar** o inicia una operación de arrastrar y colocar.

1. Según el diseño del programa, la aplicación crea un objeto `COleDataSource` o un objeto de una clase derivada de `COleDataSource`.

1. Los datos seleccionados se insertan en el origen de datos con una llamada a una de las funciones de los grupos `COleDataSource::CacheData` o `COleDataSource::DelayRenderData`.

1. La aplicación llama a la función miembro `SetClipboard` (o la función miembro `DoDragDrop` si se trata de una operación de arrastrar y colocar) que pertenece al objeto creado en el paso 3.

1. Si se trata de una operación de **cortar** o `DoDragDrop` devuelve **DROPEFFECT_MOVE**, los datos seleccionados en el paso 1 se eliminarán del documento.

Este escenario se implementa mediante los ejemplos OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md). Para cada clase derivada de `CView` de la aplicación, examine el código fuente para todas las funciones excepto `GetClipboardData` y `OnGetClipboardData`. Estas dos funciones están en las implementaciones de clase derivada `COleClientItem` o `COleServerItem`. Estos programas de ejemplo constituyen una buena muestra de cómo implementar estos conceptos.

Otra situación en la que puede que quiera crear un objeto `COleDataSource` sucede cuando modifica el comportamiento predeterminado de una operación de arrastrar y colocar. Para obtener más información, vea el artículo [arrastrar y colocar de OLE: personalización de arrastrar y colocar](drag-and-drop-ole.md#customize-drag-and-drop) .

## <a name="destroying-data-sources"></a><a name="_core_destroying_data_sources"></a>Destruir orígenes de datos

La aplicación responsable de los orígenes de datos debe destruirlos. En situaciones en las que el origen de datos se entrega a OLE, como llamar a [COleDataSource::D odragdrop](reference/coledatasource-class.md#dodragdrop), es preciso llamar a `pDataSrc->InternalRelease` . Por ejemplo:

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Si no ha entregado el origen de datos a OLE, el usuario es el responsable de destruirlo, igual que sucede con cualquier objeto habitual de C++.

Para obtener más información, vea [arrastrar y colocar](drag-and-drop-ole.md), [portapapeles](clipboard.md)y [manipular objetos de datos y orígenes de datos](data-objects-and-data-sources-manipulation.md).

## <a name="see-also"></a>Consulte también

[Objetos de datos y orígenes de datos (OLE)](data-objects-and-data-sources-ole.md)<br/>
[COleDataObject (clase)](reference/coledataobject-class.md)<br/>
[COleDataSource (clase)](reference/coledatasource-class.md)
