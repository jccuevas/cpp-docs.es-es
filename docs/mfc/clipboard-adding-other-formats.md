---
title: 'Portapapeles: Agregar otros formatos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c28fd1d628d0aed79028e43d9cce383f3acbb4ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342152"
---
# <a name="clipboard-adding-other-formats"></a>Portapapeles: Agregar otros formatos
Este tema explica cómo ampliar la lista de los formatos admitidos, especialmente para compatibilidad con OLE. El tema [Portapapeles: copias y pegar datos](../mfc/clipboard-copying-and-pasting-data.md) describe la implementación mínima necesaria para admitir copiando y pegando desde el Portapapeles. Si esto es todo lo que implemente, los únicos formatos colocados en el Portapapeles son `CF_METAFILEPICT`, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**y, posiblemente, `CF_LINKSOURCE`. Mayoría de las aplicaciones necesitará más formatos del Portapapeles que estos tres.  
  
##  <a name="_core_registering_custom_formats"></a> Registrar formatos personalizados  
 Para crear sus propios formatos personalizados, siga el mismo procedimiento que utilizaría para registrar cualquier formato de Portapapeles personalizado: pase el nombre del formato para la **RegisterClipboardFormat** funcionar y utilizar su valor devuelto como el identificador de formato.  
  
##  <a name="_core_placing_formats_on_the_clipboard"></a> Colocar formatos en el Portapapeles  
 Para agregar más formatos a los que se encuentran en el Portapapeles, debe reemplazar el `OnGetClipboardData` función en la clase derivada desde `COleClientItem` o `COleServerItem` (dependiendo de si los datos que se va a copiarse están nativo). En esta función, debe usar el siguiente procedimiento.  
  
#### <a name="to-place-formats-on-the-clipboard"></a>Para colocar formatos en el Portapapeles  
  
1.  Crear un objeto `COleDataSource`.  
  
2.  Pase este origen de datos a una función que agrega los formatos de datos nativos a la lista de los formatos admitidos por una llamada a `COleDataSource::CacheGlobalData`.  
  
3.  Agregue formatos estándar mediante una llamada a `COleDataSource::CacheGlobalData` para cada formato estándar que desee admitir.  
  
 Esta técnica se utiliza en el programa de ejemplo OLE de MFC [HIERSVR](../visual-cpp-samples.md) (examinar el `OnGetClipboardData` función miembro de la **CServerItem** clase). La única diferencia en este ejemplo es que el paso tres no está implementado porque HIERSVR es compatible con ningún otros formatos estándares.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Transferencia de datos uniformes y orígenes de datos y objetos de datos OLE](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [Funciones OLE de arrastrar y colocar](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## <a name="see-also"></a>Vea también  
 [Portapapeles: Usar el mecanismo del Portapapeles de OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

