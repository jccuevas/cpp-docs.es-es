---
title: 'Portapapeles: Copiar y pegar datos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f4a3ba23fbf6e9465d78b04fcd79758c7cae525
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060239"
---
# <a name="clipboard-copying-and-pasting-data"></a>Portapapeles: Copiar y pegar datos

Este tema describe el trabajo mínimo necesario implementar copiar a y pegar del Portapapeles en una aplicación OLE. Se recomienda que lea el [objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md) temas antes de continuar.

Para poder implementar copiar o pegar, primero debe proporcionar las funciones para administrar las opciones de copiar, cortar y pegar en el menú Edición.

##  <a name="_core_copying_or_cutting_data"></a> Copiar o cortar datos

#### <a name="to-copy-data-to-the-clipboard"></a>Para copiar datos en el Portapapeles

1. Determinar si los datos que se va a copiar son datos nativos o es un elemento incrustado o vinculado.

   - Si los datos están incrustados o vinculados, obtener un puntero a la `COleClientItem` objeto que se ha seleccionado.

   - Si los datos son nativos y la aplicación es un servidor, cree un nuevo objeto derivado de `COleServerItem` que contiene los datos seleccionados. De lo contrario, cree un `COleDataSource` objeto para los datos.

1. Llamar al elemento seleccionado `CopyToClipboard` función miembro.

1. Si el usuario selecciona una operación de cortar en lugar de una operación de copia, eliminar los datos seleccionados de la aplicación.

Para ver un ejemplo de esta secuencia, vea la `OnEditCut` y `OnEditCopy` programas de ejemplo de funciones en la aplicación OLE [OCLIENT](../visual-cpp-samples.md) y [HIERSVR](../visual-cpp-samples.md). Tenga en cuenta que estos ejemplos mantienen un puntero a los datos seleccionados actualmente, por lo que el paso 1 ya está completando.

##  <a name="_core_pasting_data"></a> Pegar datos

Pegado de datos es más complicado que copiarlo, debe elegir el formato que se usará para pegar los datos en la aplicación.

#### <a name="to-paste-data-from-the-clipboard"></a>Para pegar datos desde el Portapapeles

1. En la clase de vista, implemente `OnEditPaste` para administrar los usuarios elegir la opción Pegar en el menú Edición.

1. En el `OnEditPaste` función, cree un `COleDataObject` objeto y llamar a su `AttachClipboard` función miembro para vincular este objeto a los datos en el Portapapeles.

1. Llame a `COleDataObject::IsDataAvailable` para comprobar si un formato determinado está disponible.

   Como alternativa, puede usar `COleDataObject::BeginEnumFormats` para buscar otros formatos hasta que encuentre uno más adecuados para su aplicación.

1. La operación de pegar el formato.

Para obtener un ejemplo de cómo funciona esto, vea la implementación de la `OnEditPaste` funciones miembro en las clases de vista definidas en los programas de ejemplo OLE de MFC [OCLIENT](../visual-cpp-samples.md) y [HIERSVR](../visual-cpp-samples.md).

> [!TIP]
>  La principal ventaja de separar la operación de pegado en su propia función es que se puede usar el mismo código de pegar cuando se colocan los datos en la aplicación durante una operación de arrastrar y colocar. Al igual que en OCLIENT y HIERSVR, su `OnDrop` también puede llamar la función `DoPasteItem`, reutilizar el código escrito para implementar operaciones de pegar.

Para controlar la opción Pegado especial en el menú Edición, vea el tema [cuadros de diálogo en OLE](../mfc/dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Agregar otros formatos](../mfc/clipboard-adding-other-formats.md)

- [Transferencia de datos uniformes y orígenes de datos y objetos de datos OLE](../mfc/data-objects-and-data-sources-ole.md)

- [Arrastrar y colocar OLE](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Vea también

[Portapapeles: Usar el mecanismo del Portapapeles de OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

