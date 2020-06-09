---
title: 'Portapapeles: Copiar y pegar datos'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: ed3056ec4fb3d3098870a03522d3bf17f41fbe34
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620707"
---
# <a name="clipboard-copying-and-pasting-data"></a>Portapapeles: Copiar y pegar datos

En este tema se describe el trabajo mínimo necesario para implementar la copia y el pegado desde el portapapeles en la aplicación OLE. Se recomienda leer los temas de [objetos de datos y orígenes de datos (OLE)](data-objects-and-data-sources-ole.md) antes de continuar.

Antes de poder implementar copiar o pegar, primero debe proporcionar funciones para controlar las opciones de copiar, cortar y pegar en el menú edición.

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>Copiar o cortar datos

#### <a name="to-copy-data-to-the-clipboard"></a>Para copiar datos en el portapapeles

1. Determine si los datos que se van a copiar son datos nativos o si es un elemento vinculado o incrustado.

   - Si los datos están incrustados o vinculados, obtenga un puntero al `COleClientItem` objeto que se ha seleccionado.

   - Si los datos son nativos y la aplicación es un servidor, cree un nuevo objeto derivado de `COleServerItem` que contenga los datos seleccionados. De lo contrario, cree un `COleDataSource` objeto para los datos.

1. Llamar a la función miembro del elemento seleccionado `CopyToClipboard` .

1. Si el usuario elige una operación de cortar en lugar de una operación de copia, elimine los datos seleccionados de la aplicación.

Para ver un ejemplo de esta secuencia, vea las `OnEditCut` `OnEditCopy` funciones y en los programas de ejemplo OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md). Tenga en cuenta que estos ejemplos mantienen un puntero a los datos seleccionados actualmente, por lo que el paso 1 ya está completo.

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>Pegar datos

Pegar datos es más complicado que copiarlos, ya que debe elegir el formato que se va a usar para pegar los datos en la aplicación.

#### <a name="to-paste-data-from-the-clipboard"></a>Para pegar datos del portapapeles

1. En la clase de vista, implemente `OnEditPaste` para administrar usuarios eligiendo la opción pegar del menú edición.

1. En la `OnEditPaste` función, cree un `COleDataObject` objeto y llame a su `AttachClipboard` función miembro para vincular este objeto a los datos del portapapeles.

1. Llame `COleDataObject::IsDataAvailable` a para comprobar si un formato determinado está disponible.

   Como alternativa, puede usar `COleDataObject::BeginEnumFormats` para buscar otros formatos hasta encontrar uno más adecuado para la aplicación.

1. Pegue el formato.

Para obtener un ejemplo de cómo funciona esto, vea la implementación de las `OnEditPaste` funciones miembro en las clases de vista definidas en los programas de ejemplo OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md).

> [!TIP]
> La principal ventaja de separar la operación de pegado en su propia función es que se puede usar el mismo código de pegado cuando los datos se colocan en la aplicación durante una operación de arrastrar y colocar. Como en OCLIENT y HIERSVR, la `OnDrop` función también puede llamar a `DoPasteItem` , reutilizando el código escrito para implementar las operaciones de pegar.

Para controlar la opción Pegar especial en el menú Edición, vea los [cuadros de diálogo de temas en OLE](dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Agregar otros formatos](clipboard-adding-other-formats.md)

- [Objetos de datos OLE y orígenes de datos y transferencia de datos uniforme](data-objects-and-data-sources-ole.md)

- [Funciones OLE de arrastrar y colocar](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>Consulte también

[Portapapeles: Usar el mecanismo del Portapapeles de OLE](clipboard-using-the-ole-clipboard-mechanism.md)
