---
title: 'Portapapeles: Usar el mecanismo del Portapapeles OLE | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4996c6559ad20141fb84ed37e87fd1551e89a77b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Portapapeles: Usar el mecanismo del Portapapeles de OLE
OLE utiliza formatos estándar y algunos formatos específicos de OLE para transferir datos a través del Portapapeles.  
  
 Al cortar o copiar los datos de una aplicación, los datos se almacenan en el Portapapeles para utilizarlo más adelante en las operaciones de pegar. Estos datos están en una variedad de formatos. Cuando un usuario decide pegar datos desde el Portapapeles, la aplicación puede elegir cuál de estos formatos. La aplicación debe estar escrita para elegir el formato que proporciona la información más, a menos que el usuario solicite específicamente para un formato determinado, utilizando pegado especial. Antes de continuar, puede que desee leer la [objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md) temas. Se describen los conceptos básicos de cómo funcionan las transferencias de datos y cómo implementarlos en las aplicaciones.  
  
 Windows define varios formatos estándares que puede utilizar para transferir datos a través del Portapapeles. Estos incluyen metarchivos, texto, mapas de bits y otras personas. OLE define una serie de formatos de específicos de OLE. Para las aplicaciones que necesitan más detalle que el indicado en estos formatos estándares, es una buena idea para registrar sus propios formatos personalizados del Portapapeles. Utilice la función API de Win32 [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) hacerlo.  
  
 Por ejemplo, Microsoft Excel registra un formato personalizado para hojas de cálculo. Este formato lleva mucha más información que, por ejemplo, un mapa de bits. Cuando estos datos se pegarán en una aplicación que admita el formato de hoja de cálculo, todas las fórmulas y los valores de la hoja de cálculo se conservan y se pueden actualizar si es necesario. Microsoft Excel también coloca datos en el Portapapeles con formatos para que se puede pegar como un elemento OLE. Cualquier contenedor de documentos OLE puede pegar esta información como un elemento incrustado. Este elemento incrustado se puede cambiar con Microsoft Excel. El Portapapeles también contiene un mapa de bits simple de la imagen del intervalo seleccionado en la hoja de cálculo. Esto también se puede pegar en contenedores de documentos OLE o en los editores de mapa de bits, como Paint. Sin embargo, en el caso de un mapa de bits, hay ninguna manera para manipular los datos como una hoja de cálculo.  
  
 Para recuperar la máxima cantidad de información desde el Portapapeles, las aplicaciones deben comprobar estos formatos personalizados antes de pegar datos desde el Portapapeles.  
  
 Por ejemplo, para habilitar el comando Cortar, puede escribir a un controlador algo parecido a lo siguiente:  
  
 [!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Copiar y pegar datos](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Agregar otros formatos](../mfc/clipboard-adding-other-formats.md)  
  
-   [Usar el Portapapeles de Windows](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [Transferencia de datos uniformes y orígenes de datos y objetos de datos OLE](../mfc/data-objects-and-data-sources-ole.md)  
  
## <a name="see-also"></a>Vea también  
 [Portapapeles](../mfc/clipboard.md)

