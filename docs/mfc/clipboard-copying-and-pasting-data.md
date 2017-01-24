---
title: "Portapapeles: Copiar y pegar datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Portapapeles, copiar datos"
  - "Portapapeles, pegar"
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Portapapeles: Copiar y pegar datos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema describe el trabajo mínimo necesario implementar copiar y pegar desde el portapapeles en la aplicación OLE.  Se recomienda leer los temas de [Objetos de datos y orígenes de datos \(OLE\)](../mfc/data-objects-and-data-sources-ole.md) antes de continuar.  
  
 Antes de implementar copiar o pegar, primero debe proporcionar funciones para controlar la copia, las opciones corta, y pegue en el menú Edición.  
  
##  <a name="_core_copying_or_cutting_data"></a> Copiar o datos reduciendo  
  
#### Para copiar datos en el portapapeles  
  
1.  Determine si los datos se copiará es datos nativos o es un elemento incrustado o vinculado.  
  
    -   Si se inserta o se vincula los datos, obtenga un puntero al objeto de `COleClientItem` se ha seleccionado que.  
  
    -   Si los datos son nativo y la aplicación es un servidor, cree un nuevo objeto derivado de `COleServerItem` que contiene los datos seleccionados.  Si no, cree un objeto de `COleDataSource` para los datos.  
  
2.  Llame a la función miembro de `CopyToClipboard` del elemento seleccionado.  
  
3.  Si el usuario eligió una operación de cortar en lugar de una operación de copia, elimine los datos seleccionados de la aplicación.  
  
 Para ver un ejemplo de esta secuencia, vea **OnEditCut** y **OnEditCopy** funciona en los programas de ejemplo de OLE [OCLIENT](../top/visual-cpp-samples.md) y [HIERSVR](../top/visual-cpp-samples.md)MFC.  Observe que estos ejemplos mantienen un puntero a los datos seleccionados actualmente, por lo que el paso 1 ya se ha completado.  
  
##  <a name="_core_pasting_data"></a> Datos de pegar  
 Pegar datos es más complicado que copiándolo porque necesita elegir el formato para utilizar en pegar los datos en la aplicación.  
  
#### Para pegar datos del portapapeles  
  
1.  En la clase de vista, implementar **OnEditPaste** para controlar los usuarios que elija la opción de pegar el menú Edición.  
  
2.  En función de **OnEditPaste** , cree un objeto de `COleDataObject` y llame a su función miembro de `AttachClipboard` para vincular este objeto a los datos en el portapapeles.  
  
3.  Llame a `COleDataObject::IsDataAvailable` para comprobar si un formato determinado está disponible.  
  
     Como alternativa, puede utilizar `COleDataObject::BeginEnumFormats` para buscar otros formatos hasta encontrar uno adecuado más a la aplicación.  
  
4.  Realice pegar de formato.  
  
 Para obtener un ejemplo de cómo funciona esto, vea la de las funciones miembro de **OnEditPaste** en las clases de vista definidas en los programas de ejemplo de OLE [OCLIENT](../top/visual-cpp-samples.md) y [HIERSVR](../top/visual-cpp-samples.md)MFC.  
  
> [!TIP]
>  La ventaja principal de separar la operación de pegar en su propia función es que el mismo código de pegar puede utilizar cuando se colocan los datos en la aplicación durante una operación de arrastrar y colocar.  Como en OCLIENT e HIERSVR, la función de `OnDrop` también puede llamar **DoPasteItem**, reutilizar el código escrito a las operaciones de pegar de implementan.  
  
 Para controlar la opción de Pegado especial en el menú Edición, vea el tema [Cuadros de diálogo de OLE](../mfc/dialog-boxes-in-ole.md).  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Agregar otros formatos](../mfc/clipboard-adding-other-formats.md)  
  
-   [Objetos de datos de OLE y orígenes de datos y transferencia de datos uniforme](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [Arrastrar y colocar de OLE](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## Vea también  
 [Portapapeles: Usar el mecanismo del Portapapeles de OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)