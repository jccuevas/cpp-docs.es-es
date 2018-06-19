---
title: 'Portapapeles: Copiar y pegar datos | Documentos de Microsoft'
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
ms.openlocfilehash: bdfd43933453e44c49d713a1565ac3f71e019de4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343355"
---
# <a name="clipboard-copying-and-pasting-data"></a>Portapapeles: Copiar y pegar datos
Este tema describe el trabajo mínimo necesario para implementar copiar a y pegar desde el Portapapeles en una aplicación OLE. Se recomienda que lea la [objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md) temas antes de continuar.  
  
 Para poder implementar copiar o pegar, primero debe proporcionar funciones para controlar las opciones de copiar, cortar y pegar en el menú Edición.  
  
##  <a name="_core_copying_or_cutting_data"></a> Copiar o cortar datos  
  
#### <a name="to-copy-data-to-the-clipboard"></a>Para copiar los datos en el Portapapeles  
  
1.  Determine si los datos que se va a copiar son datos nativos o es un elemento vinculado o incrustado.  
  
    -   Si los datos se incrustados o vinculados, obtener un puntero a la `COleClientItem` objeto que se ha seleccionado.  
  
    -   Si los datos son nativos y la aplicación es un servidor, cree un nuevo objeto derivado de `COleServerItem` que contiene los datos seleccionados. De lo contrario, cree un `COleDataSource` objeto para los datos.  
  
2.  Llamar al elemento seleccionado `CopyToClipboard` función miembro.  
  
3.  Si el usuario selecciona una operación de cortar en lugar de una operación de copia, eliminar los datos seleccionados de la aplicación.  
  
 Para ver un ejemplo de esta secuencia, vea la **funciones OnEditCut** y **OnEditCopy** programas de ejemplo de las funciones de la aplicación OLE [OCLIENT](../visual-cpp-samples.md) y [HIERSVR](../visual-cpp-samples.md). Tenga en cuenta que estos ejemplos mantienen un puntero a los datos seleccionados actualmente, por lo que ya está completado el paso 1.  
  
##  <a name="_core_pasting_data"></a> Pegar datos  
 Pegar datos es más complicado que copiarlos porque debe elegir el formato que se usará para pegar los datos en la aplicación.  
  
#### <a name="to-paste-data-from-the-clipboard"></a>Para pegar datos desde el Portapapeles  
  
1.  En la clase de vista, implemente **OnEditPaste** para administrar los usuarios elegir la opción Pegar en el menú Edición.  
  
2.  En el **OnEditPaste** funcione, cree un `COleDataObject` objeto y llame a su `AttachClipboard` función de miembro para vincular este objeto a los datos en el Portapapeles.  
  
3.  Llame a `COleDataObject::IsDataAvailable` para comprobar si un formato determinado está disponible.  
  
     Como alternativa, puede usar `COleDataObject::BeginEnumFormats` para buscar otros formatos hasta que encuentre uno más adecuados para su aplicación.  
  
4.  Pegue el formato.  
  
 Para obtener un ejemplo de cómo funciona esto, vea la implementación de la **OnEditPaste** funciones miembro en las clases de vista definidas en los programas de ejemplo OLE de MFC [OCLIENT](../visual-cpp-samples.md) y [HIERSVR](../visual-cpp-samples.md).  
  
> [!TIP]
>  La ventaja principal de separar la operación de pegado en su propia función es que se puede usar el mismo código de pegar cuando se colocan los datos en la aplicación durante una operación de arrastrar y colocar. Al igual que en OCLIENT y HIERSVR, su `OnDrop` también puede llamar la función **DoPasteItem**, reutilizar el código escrito para implementar operaciones de pegar.  
  
 Para controlar la opción Pegado especial en el menú Edición, vea el tema [cuadros de diálogo en OLE](../mfc/dialog-boxes-in-ole.md).  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Agregar otros formatos](../mfc/clipboard-adding-other-formats.md)  
  
-   [Transferencia de datos uniformes y orígenes de datos y objetos de datos OLE](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [Funciones OLE de arrastrar y colocar](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## <a name="see-also"></a>Vea también  
 [Portapapeles: Usar el mecanismo del Portapapeles de OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

