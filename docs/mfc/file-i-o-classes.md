---
title: Clases de E/s de archivo
ms.date: 11/04/2016
f1_keywords:
- vc.classes.file
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
ms.openlocfilehash: 914325ec56f0cae30c7293305496d65f358f2731
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281660"
---
# <a name="file-io-classes"></a>Clases de E/S de archivos

Estas clases proporcionan una interfaz para los archivos de disco tradicionales, los archivos en memoria, secuencias activas y sockets de Windows. Todas las clases derivan de `CFile` puede utilizarse con un `CArchive` objeto que se va a realizar la serialización.

Utilice las siguientes clases, especialmente `CArchive` y `CFile`, si escribe su propio procesamiento de entrada/salida. Normalmente no es necesario derivar de estas clases. Si usa el marco de aplicación, las implementaciones predeterminadas de la **abierto** y **guardar** comandos en el **archivo** menú controlará la E/S de archivo (mediante la clase `CArchive`), como invalidar el documento `Serialize` función para proporcionar los detalles acerca de cómo serializa su contenido en un documento. Para obtener más información sobre las clases de archivo y la serialización, vea el artículo [archivos en MFC](../mfc/files-in-mfc.md) y el artículo [serialización](../mfc/serialization-in-mfc.md).

[CFile](../mfc/reference/cfile-class.md)<br/>
Proporciona una interfaz de archivo para archivos de disco binario.

[CStdioFile](../mfc/reference/cstdiofile-class.md)<br/>
Proporciona un `CFile` interfaz para los archivos de disco de la transmisión almacenada en búfer, normalmente en modo de texto.

[CMemFile](../mfc/reference/cmemfile-class.md)<br/>
Proporciona un `CFile` interfaz a los archivos en memoria.

[CSharedFile](../mfc/reference/csharedfile-class.md)<br/>
Proporciona un `CFile` interfaz a los archivos compartidos en memoria.

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
Usa COM `IStream` interfaz para proporcionar `CFile` acceso a archivos compuestos.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Proporciona un `CFile` interfaz a un Socket de Windows.

## <a name="related-classes"></a>Clases relacionadas

[CArchive](../mfc/reference/carchive-class.md)<br/>
Coopera con un `CFile` objeto para implementar el almacenamiento persistente para los objetos mediante la serialización (vea [CObject:: Serialize](../mfc/reference/cobject-class.md#serialize)).

[CArchiveException](../mfc/reference/carchiveexception-class.md)<br/>
Una excepción de archivo.

[CFileException](../mfc/reference/cfileexception-class.md)<br/>
Una excepción orientado a archivos.

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para abrir o guardar un archivo.

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
Mantiene la mayoría de la archivos usados recientemente (MRU).

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
