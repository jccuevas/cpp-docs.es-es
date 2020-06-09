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
ms.openlocfilehash: 52089364a6be423c69a7031cd0d99e1924de1444
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626064"
---
# <a name="clipboard-adding-other-formats"></a>Portapapeles: Agregar otros formatos

En este tema se explica cómo expandir la lista de formatos admitidos, especialmente para la compatibilidad con OLE. El tema [portapapeles: copiar y pegar datos](clipboard-copying-and-pasting-data.md) describe la implementación mínima necesaria para admitir la copia y el pegado desde el portapapeles. Si esto es todo lo que se implementa, los únicos formatos que se colocan en el portapapeles son **CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**y, posiblemente, **CF_LINKSOURCE**. La mayoría de las aplicaciones necesitarán más formatos en el portapapeles que en los tres.

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>Registrar formatos personalizados

Para crear sus propios formatos personalizados, siga el mismo procedimiento que usaría al registrar cualquier formato de Portapapeles personalizado: pase el nombre del formato a la función **RegisterClipboardFormat** y use su valor devuelto como identificador de formato.

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>Colocar formatos en el portapapeles

Para agregar más formatos a los colocados en el portapapeles, debe invalidar la `OnGetClipboardData` función en la clase derivada de `COleClientItem` o `COleServerItem` (dependiendo de si los datos que se van a copiar son nativos). En esta función, debe utilizar el procedimiento siguiente.

#### <a name="to-place-formats-on-the-clipboard"></a>Para colocar formatos en el portapapeles

1. Crear un objeto `COleDataSource`.

1. Pase este origen de datos a una función que agregue los formatos de datos nativos a la lista de formatos admitidos llamando a `COleDataSource::CacheGlobalData` .

1. Agregue formatos estándar llamando a `COleDataSource::CacheGlobalData` para cada formato estándar que desee admitir.

Esta técnica se usa en el programa de ejemplo OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md) (examine la `OnGetClipboardData` función miembro de la clase **CServerItem** ). La única diferencia en este ejemplo es que el paso tres no está implementado porque HIERSVR no admite ningún otro formato estándar.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Objetos de datos OLE y orígenes de datos y transferencia de datos uniforme](data-objects-and-data-sources-ole.md)

- [Funciones OLE de arrastrar y colocar](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>Consulte también

[Portapapeles: Usar el mecanismo del Portapapeles de OLE](clipboard-using-the-ole-clipboard-mechanism.md)
