---
title: Funciones OLE de arrastrar y colocar
description: Información general sobre la función de arrastrar y colocar de Microsoft Foundation Classes (MFC) OLE, cómo implementar un origen de colocación, un destino de colocación y cómo personalizar la función de arrastrar y colocar.
ms.date: 02/09/2020
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
ms.openlocfilehash: 23680765377d325bdc1f8878daf4d4fc553a1304
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623185"
---
# <a name="ole-drag-and-drop"></a>Funciones OLE de arrastrar y colocar

La característica de arrastrar y colocar de OLE es principalmente un acceso directo para copiar y pegar datos. Al usar el portapapeles para copiar o pegar datos, se requieren varios pasos. Seleccione los datos y elija **cortar** o **copiar** en el menú **edición** . A continuación, vaya a la aplicación o ventana de destino y coloque el cursor en la ubicación de destino. Por último, elija **Editar**  >  **pegar** en el menú.

La característica OLE de arrastrar y colocar es diferente del mecanismo de arrastrar y colocar del administrador de archivos. El administrador de archivos solo puede controlar nombres de archivo y está diseñado específicamente para pasar nombres de archivo a aplicaciones. Arrastrar y colocar en OLE es mucho más general. Permite arrastrar y colocar los datos que también se pueden colocar en el portapapeles.

Al usar arrastrar y colocar de OLE, se quitan dos pasos del proceso. Seleccione los datos de la ventana de código fuente (el "origen de colocación") y, a continuación, arrástrelo hasta el destino (el "destino de colocación"). Para colocarlo, suelte el botón del mouse. La operación elimina la necesidad de menús, y es más rápido que la secuencia de copiar y pegar. Hay solo un requisito: el origen de colocación y el destino de colocación deben estar abiertos y, al menos, parcialmente visibles en la pantalla.

Con arrastrar y colocar de OLE, los datos se pueden transferir fácilmente de una ubicación a otra: dentro de un documento, entre distintos documentos o entre aplicaciones. Se puede implementar en un contenedor o en una aplicación de servidor. Cualquier aplicación podría ser un origen de colocación, un destino de colocación o ambos. Si una aplicación implementa tanto la compatibilidad con el origen como el destino de Drop-Source, puede arrastrar y colocar entre ventanas secundarias o dentro de una ventana. Esta característica hace que la aplicación sea mucho más fácil de usar.

Los artículos [objetos de datos y orígenes de datos (OLE)](data-objects-and-data-sources-ole.md) explican cómo implementar la transferencia de datos en las aplicaciones. También es útil examinar los ejemplos OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md).

## <a name="implement-a-drop-source"></a><a name="implement-a-drop-source"></a>Implementar un origen de colocación

Para que la aplicación proporcione datos a una operación de arrastrar y colocar, se implementa un origen de colocación. La implementación básica de un origen de colocación es relativamente sencilla. El primer paso consiste en determinar qué eventos inician una operación de arrastre. Las directrices de interfaz de usuario recomendadas definen el comienzo de una operación de arrastre como cuando se produce un evento de **WM_LBUTTONDOWN** en un punto dentro de algunos datos seleccionados. Los ejemplos OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md) siguen estas instrucciones.

Si la aplicación es un contenedor y los datos seleccionados son un objeto vinculado o incrustado de tipo `COleClientItem` , llame a su `DoDragDrop` función miembro. En caso contrario, construya un `COleDataSource` objeto, Inicialícelo con la selección y llame a la función miembro del objeto de origen de datos `DoDragDrop` . Si la aplicación es un servidor, use `COleServerItem::DoDragDrop` . Para obtener información sobre cómo personalizar el comportamiento estándar de arrastrar y colocar, consulte la sección [Personalización de arrastrar y colocar](#customize-drag-and-drop).

Si `DoDragDrop` devuelve **DROPEFFECT_MOVE**, elimine inmediatamente los datos de origen del documento de origen. Ningún otro valor devuelto de `DoDragDrop` tiene ningún efecto en un origen de colocación.

Para obtener más información, vea objetos de datos [y orígenes de datos OLE: creación y destrucción](data-objects-and-data-sources-creation-and-destruction.md) , y orígenes de datos [y objetos de datos OLE: manipulación](data-objects-and-data-sources-manipulation.md)\.

## <a name="implement-a-drop-target"></a><a name="implement-a-drop-target"></a>Implementar un destino de colocación

Se tarda un poco más en implementar un destino de colocación que un origen de colocación, pero sigue siendo relativamente sencillo.

### <a name="to-implement-an-ole-drop-target"></a>Para implementar un destino de colocación OLE

1. Si aún no está allí, agregue una llamada a `AfxOleInit` en la función miembro de la aplicación `InitInstance` . Esta llamada es necesaria para inicializar las bibliotecas OLE.

1. Agregue una variable miembro a cada vista de la aplicación que desee que sea un destino de colocación. Esta variable miembro debe ser de tipo `COleDropTarget` o una clase derivada de ella.

1. Desde la función de la clase de vista que controla el mensaje de **WM_CREATE** (normalmente `OnCreate` ), llame a la función miembro de la nueva variable miembro `Register` . `Revoke`se le llamará automáticamente cuando se destruya la vista.

1. Invalide las siguientes funciones. Si desea el mismo comportamiento en toda la aplicación, invalide estas funciones en la clase de vista. Si desea modificar el comportamiento en casos aislados o desea habilitar la colocación en distintas `CView` ventanas, invalide estas funciones en la `COleDropTarget` clase derivada de.

   | Invalidar | Para permitir |
   | -------- | -------- |
   | `OnDragEnter` | Las operaciones de eliminación se producen en la ventana. Se llama cuando el cursor entra por primera vez en la ventana. |
   | `OnDragLeave` | Comportamiento especial cuando la operación de arrastrar sale de la ventana especificada. |
   | `OnDragOver` | Las operaciones de eliminación se producen en la ventana. Se le llama cuando se arrastra el cursor por la ventana. |
   | `OnDrop` | Control de los datos que se van a colocar en la ventana especificada. |
   | `OnScrollBy` | Comportamiento especial para cuando el desplazamiento es necesario en la ventana de destino. |

Vea MAINVIEW. Archivo CPP que forma parte del ejemplo de OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) para obtener un ejemplo de cómo funcionan conjuntamente estas funciones.

Para obtener más información, vea objetos de datos [y orígenes de datos OLE: creación y destrucción](data-objects-and-data-sources-creation-and-destruction.md) , y orígenes de datos [y objetos de datos OLE: manipulación](data-objects-and-data-sources-manipulation.md)\.

## <a name="customize-drag-and-drop"></a><a name="customize-drag-and-drop"></a>Personalización de arrastrar y colocar

La implementación predeterminada de la característica de arrastrar y colocar es suficiente para la mayoría de las aplicaciones. Sin embargo, algunas aplicaciones pueden requerir que se cambie este comportamiento estándar. En esta sección se explican los pasos necesarios para cambiar estos valores predeterminados. Puede utilizar esta técnica para crear aplicaciones que no admitan documentos compuestos en orígenes de colocación.

Si está personalizando el comportamiento estándar de arrastrar y colocar de OLE, o tiene una aplicación que no es de OLE, debe crear un `COleDataSource` objeto que contenga los datos. Cuando el usuario inicia una operación de arrastrar y colocar, el código debe llamar a la `DoDragDrop` función desde este objeto en lugar de hacerlo desde otras clases que admitan las operaciones de arrastrar y colocar.

Opcionalmente, puede crear un `COleDropSource` objeto para controlar la eliminación y reemplazar algunas de sus funciones según el tipo de comportamiento que desee cambiar. A continuación, este objeto de origen de colocación se pasa a `COleDataSource::DoDragDrop` para cambiar el comportamiento predeterminado de estas funciones. Estas diferentes opciones permiten una gran flexibilidad en el modo en que se admiten las operaciones de arrastrar y colocar en la aplicación. Para obtener más información sobre los orígenes de datos, vea el artículo [objetos de datos y orígenes de datos (OLE)](data-objects-and-data-sources-ole.md).

Puede invalidar las siguientes funciones para personalizar las operaciones de arrastrar y colocar:

| Invalidar | Para personalizar |
| -------- | ------------ |
| `OnBeginDrag` | Cómo comienza la operación de arrastre después de llamar a `DoDragDrop` . |
| `GiveFeedback` | Comentarios visuales, como la apariencia del cursor, para distintos resultados de la eliminación. |
| `QueryContinueDrag` | Finalización de una operación de arrastrar y colocar. Esta función permite comprobar los Estados de las teclas modificadoras durante la operación de arrastre. |

## <a name="see-also"></a>Consulte también

[OLE](ole-in-mfc.md)\
[Objetos de datos y orígenes de datos OLE](data-objects-and-data-sources-ole.md)\
[Objetos de datos OLE y orígenes de datos: creación y destrucción](data-objects-and-data-sources-creation-and-destruction.md)\
[Objetos de datos OLE y orígenes de datos: manipulación](data-objects-and-data-sources-manipulation.md)\
[COleClientItem::D oDragDrop](reference/coleclientitem-class.md#dodragdrop)\
[COleDataSource (clase)](reference/coledatasource-class.md)\
[COleDataSource::D oDragDrop](reference/coledatasource-class.md#dodragdrop)\
[Clase COleDropSource](reference/coledropsource-class.md)\
[Clase COleDropTarget](reference/coledroptarget-class.md)\
[CView:: OnDragLeave](reference/cview-class.md#ondragleave)
