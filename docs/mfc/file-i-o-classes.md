---
title: Clases de e/s de archivo
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
ms.openlocfilehash: 2fcf4dfc1388df0df2bc25928ec8541486c6bb2d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615670"
---
# <a name="file-io-classes"></a>Clases de E/S de archivos

Estas clases proporcionan una interfaz para los archivos de disco tradicionales, los archivos en memoria, las secuencias activas y Windows Sockets. Todas las clases derivadas de `CFile` se pueden utilizar con un `CArchive` objeto para realizar la serialización.

Use las clases siguientes, especialmente `CArchive` y `CFile` , si escribe su propio procesamiento de entrada/salida. Normalmente no es necesario derivar de estas clases. Si usa el marco de trabajo de la aplicación, las implementaciones predeterminadas de los comandos **abrir** y **Guardar** en el menú **archivo** controlarán la e/s de archivos (mediante la clase `CArchive` ), siempre y cuando invalide la función del documento `Serialize` para proporcionar detalles sobre cómo un documento serializa su contenido. Para obtener más información sobre las clases de archivo y la serialización, vea el artículo [archivos en MFC](files-in-mfc.md) y el artículo [serialización](serialization-in-mfc.md).

[CFile](reference/cfile-class.md)<br/>
Proporciona una interfaz de archivo para archivos de disco binarios.

[CStdioFile](reference/cstdiofile-class.md)<br/>
Proporciona una `CFile` interfaz para los archivos de disco de secuencia almacenados en búfer, normalmente en modo de texto.

[CMemFile](reference/cmemfile-class.md)<br/>
Proporciona una `CFile` interfaz para los archivos en memoria.

[CSharedFile](reference/csharedfile-class.md)<br/>
Proporciona una `CFile` interfaz para los archivos en memoria compartidos.

[COleStreamFile](reference/colestreamfile-class.md)<br/>
Utiliza la `IStream` interfaz com para proporcionar `CFile` acceso a los archivos compuestos.

[CSocketFile](reference/csocketfile-class.md)<br/>
Proporciona una `CFile` interfaz a un socket de Windows.

## <a name="related-classes"></a>Clases relacionadas

[CArchive](reference/carchive-class.md)<br/>
Coopera con un `CFile` objeto para implementar el almacenamiento persistente para los objetos a través de la serialización (vea [CObject:: Serialize](reference/cobject-class.md#serialize)).

[CArchiveException](reference/carchiveexception-class.md)<br/>
Excepción de archivo.

[CFileException](reference/cfileexception-class.md)<br/>
Excepción orientada a archivos.

[CFileDialog](reference/cfiledialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para abrir o guardar un archivo.

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
Mantiene la lista de archivos usados más recientemente (MRU).

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
