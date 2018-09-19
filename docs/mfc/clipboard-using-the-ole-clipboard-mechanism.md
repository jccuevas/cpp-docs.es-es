---
title: 'Portapapeles: Usar el mecanismo del Portapapeles OLE | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d37618dccabd576a67c8b82a8b8ab38246254070
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214710"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Portapapeles: Usar el mecanismo del Portapapeles de OLE
OLE utiliza formatos estándar y algunos formatos específicos de OLE para transferir datos a través del Portapapeles.  
  
 Al cortar o copiar datos desde una aplicación, los datos se almacenan en el Portapapeles para su uso posterior en las operaciones de pegar. Estos datos están en una variedad de formatos. Cuando un usuario elige pegar datos desde el Portapapeles, la aplicación puede elegir cuál de estos formatos para usar. La aplicación debe escribirse para elegir el formato que proporciona la máxima información posible, a menos que el usuario solicite específicamente para un formato determinado, mediante el pegado especial. Antes de continuar, es posible que desee leer el [objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md) temas. Describen los aspectos básicos de cómo funcionan las transferencias de datos y cómo implementarlos en sus aplicaciones.  
  
 Windows define una serie de los formatos estándar que puede usarse para transferir datos a través del Portapapeles. Estos incluyen metarchivos, texto, mapas de bits y otros usuarios. OLE define un número de formatos de específicos de OLE. Para las aplicaciones que necesitan más detalles que determinado los formatos estándar, es una buena idea registrar sus propios formatos personalizados del Portapapeles. Use la función de la API Win32 [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) para hacerlo.  
  
 Por ejemplo, Microsoft Excel registra un formato personalizado para hojas de cálculo. Este formato lleva mucho más información que, por ejemplo, un mapa de bits. Cuando estos datos se pegarán en una aplicación que admita el formato de hoja de cálculo, todas las fórmulas y los valores de la hoja de cálculo se conservan y se pueden actualizar si es necesario. Microsoft Excel también coloca datos en el Portapapeles con formatos para que se puede pegar como un elemento OLE. Cualquier contenedor de documentos OLE puede pegar esta información como un elemento incrustado. Este elemento incrustado se puede cambiar con Microsoft Excel. El Portapapeles también contiene un mapa de bits sencilla de la imagen del intervalo seleccionado en la hoja de cálculo. Esto también se puede pegar en contenedores de documentos OLE o en los editores de mapa de bits, como la pintura. Sin embargo, en el caso de un mapa de bits, hay ninguna manera de manipular los datos como una hoja de cálculo.  
  
 Para recuperar la cantidad máxima de información desde el Portapapeles, las aplicaciones deben comprobar estos formatos personalizados antes de pegar datos desde el Portapapeles.  
  
 Por ejemplo, para habilitar el comando Cortar, podría escribir a un controlador de algo parecido a lo siguiente:  
  
 [!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre  
  
-   [Copiar y pegar datos](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Agregar otros formatos](../mfc/clipboard-adding-other-formats.md)  
  
-   [Usar el Portapapeles de Windows](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [Transferencia de datos uniformes y orígenes de datos y objetos de datos OLE](../mfc/data-objects-and-data-sources-ole.md)  
  
## <a name="see-also"></a>Vea también  
 [Portapapeles](../mfc/clipboard.md)

