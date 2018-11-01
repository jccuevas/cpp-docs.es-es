---
title: Clases de excepciones
ms.date: 11/04/2016
f1_keywords:
- vc.classes.exception
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
ms.openlocfilehash: fad88fa36c64bd9d8ca28135c09a3f0ce8fe3c0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441943"
---
# <a name="exception-classes"></a>Clases de excepciones

La biblioteca de clases proporciona un mecanismo de control de excepciones basado en la clase `CException`. El marco de aplicación usa las excepciones en su código; También puede usar en la suya. Para obtener más información, vea el artículo [excepciones](../mfc/exception-handling-in-mfc.md). Puede derivar sus propios tipos de excepción desde `CException`.

MFC proporciona una clase de excepción de la que puede derivar su propia excepción, así como las clases de excepción para todas las excepciones que admite.

[CException](../mfc/reference/cexception-class.md)<br/>
La clase base de las excepciones.

[CArchiveException](../mfc/reference/carchiveexception-class.md)<br/>
Una excepción de archivo.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Una excepción resultante de un error en una operación de base de datos DAO.

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
Una excepción resultante de un error en el procesamiento de base de datos ODBC.

[CFileException](../mfc/reference/cfileexception-class.md)<br/>
Una excepción orientado a archivos.

[CMemoryException](../mfc/reference/cmemoryexception-class.md)<br/>
Una excepción de memoria insuficiente.

[CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)<br/>
Una excepción derivados del uso de una función no admitida.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Una excepción resultante de un error en el procesamiento de OLE. Esta clase se utiliza por contenedores y servidores.

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
Una excepción resultante de un error durante la automatización. Excepciones de automatización son iniciadas por servidores de automatización y detectadas por los clientes de automatización.

[CResourceException](../mfc/reference/cresourceexception-class.md)<br/>
Una excepción resultante de un error al cargar un recurso de Windows.

[CUserException](../mfc/reference/cuserexception-class.md)<br/>
Una excepción que se usa para detener una operación iniciada por el usuario. Normalmente, el usuario ha notificado del problema antes de que se produce esta excepción.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

