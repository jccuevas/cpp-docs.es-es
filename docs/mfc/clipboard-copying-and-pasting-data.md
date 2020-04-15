---
title: 'Portapapeles: Copiar y pegar datos'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: 74348dd3e790cceada9aafd718464694997316ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374567"
---
# <a name="clipboard-copying-and-pasting-data"></a>Portapapeles: Copiar y pegar datos

En este tema se describe el trabajo mínimo necesario para implementar la copia y el pegado desde el Portapapeles en la aplicación OLE. Se recomienda leer los temas Objetos de datos y orígenes de [datos (OLE)](../mfc/data-objects-and-data-sources-ole.md) antes de continuar.

Para poder implementar la copia o el pegado, primero debe proporcionar funciones para controlar las opciones Copiar, Cortar y Pegar en el menú Editar.

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>Copiar o cortar datos

#### <a name="to-copy-data-to-the-clipboard"></a>Para copiar datos en el Portapapeles

1. Determine si los datos que se van a copiar son datos nativos o es un elemento incrustado o vinculado.

   - Si los datos están incrustados o vinculados, obtenga un puntero al `COleClientItem` objeto que se ha seleccionado.

   - Si los datos son nativos y la aplicación es `COleServerItem` un servidor, cree un nuevo objeto derivado de la que contiene los datos seleccionados. De lo `COleDataSource` contrario, cree un objeto para los datos.

1. Llame a la `CopyToClipboard` función miembro del elemento seleccionado.

1. Si el usuario eligió una operación de corte en lugar de una operación de copia, elimine los datos seleccionados de la aplicación.

Para ver un ejemplo de `OnEditCut` esta `OnEditCopy` secuencia, vea y funciones en los programas de ejemplo OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md). Tenga en cuenta que estos ejemplos mantienen un puntero a los datos seleccionados actualmente, por lo que el paso 1 ya está completo.

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>Pegar datos

Pegar datos es más complicado que copiarlos porque debe elegir el formato que se usará para pegar los datos en la aplicación.

#### <a name="to-paste-data-from-the-clipboard"></a>Para pegar datos desde el Portapapeles

1. En la clase `OnEditPaste` de vista, implemente para controlar a los usuarios que elijan la opción Pegar en el menú Edición.

1. En `OnEditPaste` la función, cree `COleDataObject` `AttachClipboard` un objeto y llame a su función miembro para vincular este objeto a los datos del Portapapeles.

1. Llame `COleDataObject::IsDataAvailable` para comprobar si un formato determinado está disponible.

   Como alternativa, puede `COleDataObject::BeginEnumFormats` usar para buscar otros formatos hasta que encuentre uno más adecuado para su aplicación.

1. Realice la pasta del formato.

Para obtener un ejemplo de cómo funciona `OnEditPaste` esto, vea la implementación de las funciones miembro en las clases de vista definidas en los programas de ejemplo OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md).

> [!TIP]
> La principal ventaja de separar la operación de pegar en su propia función es que se puede usar el mismo código de pegado cuando se quitan datos en la aplicación durante una operación de arrastrar y colocar. Al igual que en OCLIENT `OnDrop` y HIERSVR, la función también puede llamar, `DoPasteItem`reutilizando el código escrito para implementar operaciones de pegado.

Para controlar la opción Pegar especial del menú Edición, vea el tema [Cuadros](../mfc/dialog-boxes-in-ole.md)de diálogo en OLE .

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Adición de otros formatos](../mfc/clipboard-adding-other-formats.md)

- [Objetos de datos OLE y orígenes de datos y transferencia de datos uniforme](../mfc/data-objects-and-data-sources-ole.md)

- [Funciones OLE de arrastrar y colocar](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Consulte también

[Portapapeles: Usar el mecanismo del Portapapeles de OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
