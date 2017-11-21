---
title: "Omitir el mecanismo de serialización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b0beb14c2ddb159616f7cbb34b83b68e84ef0a1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="bypassing-the-serialization-mechanism"></a>Omitir el mecanismo de serialización
Como ha visto, el marco de trabajo proporciona una manera predeterminada para leer y escribir datos en y desde archivos. La serialización a través de un objeto de almacenamiento se adapte a las necesidades de una gran cantidad de aplicaciones. Este tipo de aplicación lee un archivo completamente en la memoria, permite al usuario actualizar el archivo y, a continuación, escribe la versión actualizada en el disco de nuevo.  
  
 Sin embargo, algunas aplicaciones operan sobre datos de forma muy diferente, y para estas aplicaciones no es adecuada la serialización a través de un archivo. Algunos ejemplos son programas de base de datos, los programas que sólo modifican partes de archivos de gran tamaño, los programas que escriben archivos de sólo texto y programas que comparten los archivos de datos.  
  
 En estos casos, puede reemplazar el [Serialize](../mfc/reference/cobject-class.md#serialize) función de forma diferente para mediar acciones de archivo a través de un [CFile](../mfc/reference/cfile-class.md) objeto en lugar de un [CArchive](../mfc/reference/carchive-class.md) objeto.  
  
 Puede usar el **abrir**, **lectura**, **escribir**, **cerrar**, y `Seek` funciones miembro de clase `CFile` para abrir un archivo , mueva el puntero de archivo (Buscar) a un momento concreto en el archivo, leer un registro (un número especificado de bytes) en ese momento, permitir al usuario actualizar el registro, a continuación, buscar en el mismo punto y volver a escribir el registro en el archivo. El marco de trabajo abrirá el archivo automáticamente y puede usar el `GetFile` función miembro de clase `CArchive` para obtener un puntero a la `CFile` objeto. Para su uso más sofisticado y flexible, puede invalidar la [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) y [OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument) funciones miembro de clase `CWinApp`. Para obtener más información, vea la clase [CFile](../mfc/reference/cfile-class.md) en el *referencia de MFC*.  
  
 En este escenario, su `Serialize` invalidación no hace nada, a menos que, por ejemplo, desea tener leer y escribir un encabezado de archivo para mantener actualizados cuando se cierra el documento.  
  
## <a name="see-also"></a>Vea también  
 [Uso de documentos](../mfc/using-documents.md)

