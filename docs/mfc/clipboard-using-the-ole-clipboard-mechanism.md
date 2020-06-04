---
title: 'Portapapeles: Usar el mecanismo del portapapeles OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
ms.openlocfilehash: 0f2c10f4a88b723d1ab9f4bb0ca903987359c9fd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508908"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Portapapeles: Usar el mecanismo del portapapeles OLE

OLE usa formatos estándar y algunos formatos específicos de OLE para transferir datos a través del portapapeles.

Al cortar o copiar datos de una aplicación, los datos se almacenan en el portapapeles para su uso posterior en operaciones de pegado. Estos datos están en una variedad de formatos. Cuando un usuario elige pegar datos del portapapeles, la aplicación puede elegir cuál de estos formatos usar. La aplicación debe escribirse para elegir el formato que proporciona la mayor cantidad de información, a menos que el usuario solicite específicamente un formato determinado, mediante pegar especial. Antes de continuar, puede que desee leer los temas de [objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md) . Describen los aspectos básicos de cómo funcionan las transferencias de datos y cómo implementarlas en las aplicaciones.

Windows define una serie de formatos estándar que se pueden usar para transferir datos a través del portapapeles. Entre ellos se incluyen los metaarchivos, el texto, los mapas de bits y otros elementos. OLE define también una serie de formatos específicos de OLE. En el caso de las aplicaciones que necesitan más detalles de los proporcionados por estos formatos estándar, es una buena idea registrar sus propios formatos de Portapapeles personalizados. Para ello, utilice la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) de la API de Win32.

Por ejemplo, Microsoft Excel registra un formato personalizado para las hojas de cálculo. Este formato contiene mucha más información que, por ejemplo, un mapa de bits. Cuando estos datos se pegan en una aplicación que admite el formato de hoja de cálculo, todas las fórmulas y los valores de la hoja de cálculo se conservan y se pueden actualizar si es necesario. Microsoft Excel también coloca los datos en el portapapeles en formatos para que pueda pegarse como un elemento OLE. Cualquier contenedor de documentos OLE puede pegar esta información como un elemento incrustado. Este elemento incrustado se puede cambiar con Microsoft Excel. El portapapeles también contiene un mapa de bits sencillo de la imagen del rango seleccionado en la hoja de cálculo. También se puede pegar en contenedores de documentos OLE o en editores de mapas de bits, como Paint. Sin embargo, en el caso de un mapa de bits, no hay forma de manipular los datos como una hoja de cálculo.

Para recuperar la cantidad máxima de información del portapapeles, las aplicaciones deben comprobar estos formatos personalizados antes de pegar los datos del portapapeles.

Por ejemplo, para habilitar el comando cortar, puede escribir un controlador similar al siguiente:

[!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Copiar y pegar datos](../mfc/clipboard-copying-and-pasting-data.md)

- [Agregar otros formatos](../mfc/clipboard-adding-other-formats.md)

- [Usar el portapapeles de Windows](../mfc/clipboard-using-the-windows-clipboard.md)

- [OLE](../mfc/ole-background.md)

- [Objetos de datos OLE y orígenes de datos y transferencia de datos uniforme](../mfc/data-objects-and-data-sources-ole.md)

## <a name="see-also"></a>Vea también

[Portapapeles](../mfc/clipboard.md)
