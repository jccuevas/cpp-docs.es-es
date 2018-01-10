---
title: Arrastrar y colocar (OLE) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a852e597c06a08c3e9eb83731dc7da7df077435
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="drag-and-drop-ole"></a>Arrastrar y colocar (OLE)
La característica de arrastrar y colocar de OLE es principalmente un acceso directo para copiar y pegar los datos. Al usar el Portapapeles para copiar o pegar los datos, una serie de pasos es necesaria. Seleccione los datos, haga clic en **cortar** o **copia** desde el **editar** menú, mover en el archivo de destino, la ventana o la aplicación, coloque el cursor en la ubicación deseada y haga clic en **Pegar** desde el **editar** menú.  
  
 Funciones OLE de arrastrar y colocar es diferente del mecanismo de arrastrar y colocar del Administrador de archivos, que solo se puede controlar los nombres de archivo y está diseñado específicamente para pasar los nombres de archivo a las aplicaciones. Funciones OLE de arrastrar y colocar es mucho más general. Permite arrastrar y colocar los datos que también pudieron colocarse en el Portapapeles.  
  
 Cuando usa funciones OLE de arrastrar y colocar, quitar dos pasos del proceso. Seleccionar los datos de la ventana de código fuente (el "origen de colocación"), arrástrelo hasta el destino deseado (el "destino de colocación") y se quita al soltar el botón del mouse. La operación elimina la necesidad de los menús y es más rápida que la secuencia de copiar y pegar. El único requisito es que el origen de colocación y el destino de colocación deben estar abiertas y al menos parcialmente visible en la pantalla.  
  
 Usar funciones OLE de arrastrar y colocar, datos pueden transferirse desde una ubicación a otra dentro de un documento, entre distintos documentos o entre aplicaciones. Se puede implementar en un contenedor o una aplicación de servidor y cualquier aplicación puede ser un origen de colocación, un destino para colocar o ambos. Si una aplicación tiene implementada la compatibilidad necesaria origen de colocación y el destino de colocación, arrastrar y colocar está habilitado entre ventanas secundarias o dentro de una ventana. Esta característica puede hacer que la aplicación son mucho más fáciles de usar.  
  
 Si solo desea utilizar las funciones de arrastrar y colocar de OLE, consulte [arrastrar y colocar: personalización](../mfc/drag-and-drop-customizing.md). Puede utilizar las técnicas explicadas en este artículo para que las aplicaciones de OLE no eliminar orígenes. El artículo [arrastrar y colocar: implementar un destino de Drop](../mfc/drag-and-drop-implementing-a-drop-target.md) describe cómo implementar la compatibilidad de destino de OLE y aplicaciones no compatibles con OLE. También le resultará útil examinar los ejemplos OLE de MFC [OCLIENT](../visual-cpp-samples.md) y [HIERSVR](../visual-cpp-samples.md).  
  
 Si no ha leído el [objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md) familia de artículos, puede que desee hacerlo ahora. Estos artículos explican los conceptos básicos de transferencia de datos y cómo implementarla en las aplicaciones.  
  
 Para obtener más información acerca de arrastrar y colocar, vea:  
  
-   [Arrastrar y colocar: Implementar un origen de colocación](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [Arrastrar y colocar: Implementar un destino de colocación](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [Arrastrar y colocar: Personalizar](../mfc/drag-and-drop-customizing.md)  
  
## <a name="see-also"></a>Vea también  
 [OLE](../mfc/ole-in-mfc.md)   
 [Objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md)

