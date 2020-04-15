---
title: 'Portapapeles: Agregar otros formatos'
ms.date: 11/04/2016
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
ms.openlocfilehash: 6f4e159cc1b6918843d4a164dcca88500eb7b038
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374609"
---
# <a name="clipboard-adding-other-formats"></a>Portapapeles: Agregar otros formatos

En este tema se explica cómo expandir la lista de formatos admitidos, especialmente para la compatibilidad con OLE. El tema [Portapapeles: Copiar y pegar datos](../mfc/clipboard-copying-and-pasting-data.md) describe la implementación mínima necesaria para admitir la copia y pegado desde el Portapapeles. Si esto es todo lo que implementa, los únicos formatos colocados en el Portapapeles son **CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**, y posiblemente **CF_LINKSOURCE**. La mayoría de las aplicaciones necesitarán más formatos en el Portapapeles que estos tres.

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>Registro de formatos personalizados

Para crear sus propios formatos personalizados, siga el mismo procedimiento que usaría al registrar cualquier formato de Portapapeles personalizado: pase el nombre del formato a la función **RegisterClipboardFormat** y use su valor devuelto como identificador de formato.

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>Colocación de formatos en el Portapapeles

Para agregar más formatos a los colocados `OnGetClipboardData` en el Portapapeles, `COleClientItem` `COleServerItem` debe invalidar la función en la clase derivada de cualquiera o (dependiendo de si los datos que se van a copiar son nativos). En esta función, debe utilizar el siguiente procedimiento.

#### <a name="to-place-formats-on-the-clipboard"></a>Para colocar formatos en el Portapapeles

1. Crear un objeto `COleDataSource`.

1. Pase este origen de datos a una función que agregue los `COleDataSource::CacheGlobalData`formatos de datos nativos a la lista de formatos admitidos llamando a .

1. Agregue formatos `COleDataSource::CacheGlobalData` estándar llamando a cada formato estándar que desee admitir.

Esta técnica se utiliza en el programa de `OnGetClipboardData` ejemplo OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md) (examinar la función miembro de la **CServerItem** clase). La única diferencia en este ejemplo es que el paso tres no se implementa porque HIERSVR no admite otros formatos estándar.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Objetos de datos OLE y orígenes de datos y transferencia de datos uniforme](../mfc/data-objects-and-data-sources-ole.md)

- [Funciones OLE de arrastrar y colocar](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Consulte también

[Portapapeles: Usar el mecanismo del Portapapeles de OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
