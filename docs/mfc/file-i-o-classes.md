---
title: -O clases de archivos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.file
dev_langs:
- C++
helpviewer_keywords:
- disk file classes [MFC]
- stdio classes [MFC]
- OLE streams [MFC]
- I/O [MFC], MFC classes
- translated stream classes [MFC]
- file I/O classes [MFC]
- I/O [MFC], classes
- sockets classes [MFC]
- stream classes [MFC]
- memory file classes [MFC]
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 454e64d67321282030126d2aab023e9f587c1cca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="file-io-classes"></a>Clases de E/S de archivos
Estas clases proporcionan una interfaz para los archivos de disco tradicional, en la memoria de archivos, secuencias activas y sockets de Windows. Todas las clases derivan de `CFile` puede utilizarse con un `CArchive` objeto que se va a realizar la serialización.  
  
 Utilice las siguientes clases, especialmente `CArchive` y `CFile`, si escribe su propio procesamiento de entrada/salida. Normalmente no es necesario derivar de estas clases. Si utiliza el marco de aplicación, las implementaciones predeterminadas de la **abiertos** y **guardar** comandos en el **archivo** menú controlará la E/S de archivos (mediante la clase `CArchive`), siempre y cuando se reemplaza el documento `Serialize` función para proporcionar detalles sobre cómo serializa su contenido en un documento. Para obtener más información sobre las clases de archivo y la serialización, vea el artículo [archivos en MFC](../mfc/files-in-mfc.md) y el artículo [serialización](../mfc/serialization-in-mfc.md).  
  
 [CFile](../mfc/reference/cfile-class.md)  
 Proporciona una interfaz de archivo a los archivos binarios de disco.  
  
 [CStdioFile](../mfc/reference/cstdiofile-class.md)  
 Proporciona un `CFile` interfaz a los archivos de disco de transmisión almacenada en búfer, normalmente en modo de texto.  
  
 [CMemFile](../mfc/reference/cmemfile-class.md)  
 Proporciona un `CFile` interfaz a los archivos en memoria.  
  
 [CSharedFile](../mfc/reference/csharedfile-class.md)  
 Proporciona un `CFile` interfaz a los archivos compartidos en memoria.  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 Utiliza el COM `IStream` interfaz para proporcionar `CFile` acceso a archivos compuestos.  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 Proporciona un `CFile` interfaz para un Socket de Windows.  
  
## <a name="related-classes"></a>Clases relacionadas  
 [CArchive](../mfc/reference/carchive-class.md)  
 Coopera con un `CFile` objeto que se va a implementar el almacenamiento persistente para los objetos mediante la serialización (vea [CObject:: Serialize](../mfc/reference/cobject-class.md#serialize)).  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 Una excepción de archivo.  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 Una excepción orientada a servicios de archivo.  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 Proporciona un cuadro de diálogo estándar para abrir o guardar un archivo.  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 Mantiene la mayoría de la archivos usados recientemente (MRU).  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

