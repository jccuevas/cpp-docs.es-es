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
ms.openlocfilehash: 907b34b12ffdaa70c4377a1012a66662fbba12d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619519"
---
# <a name="exception-classes"></a>Clases de excepciones

La biblioteca de clases proporciona un mecanismo de control de excepciones basado en la clase `CException` . El marco de trabajo de la aplicación utiliza excepciones en su código. también puede utilizarlos en el suyo. Para obtener más información, vea el artículo [excepciones](exception-handling-in-mfc.md). Puede derivar sus propios tipos de excepción de `CException` .

MFC proporciona una clase de excepción de la que puede derivar su propia excepción, así como clases de excepción para todas las excepciones que admite.

[CException](reference/cexception-class.md)<br/>
La clase base de las excepciones.

[CArchiveException](reference/carchiveexception-class.md)<br/>
Excepción de archivo.

[CDaoException](reference/cdaoexception-class.md)<br/>
Excepción generada por un error en una operación de base de datos DAO.

[CDBException](reference/cdbexception-class.md)<br/>
Excepción que se produce a causa de un error en el procesamiento de la base de datos ODBC.

[CFileException](reference/cfileexception-class.md)<br/>
Excepción orientada a archivos.

[CMemoryException](reference/cmemoryexception-class.md)<br/>
Excepción de memoria insuficiente.

[CNotSupportedException](reference/cnotsupportedexception-class.md)<br/>
Excepción resultante de usar una característica no admitida.

[COleException](reference/coleexception-class.md)<br/>
Excepción generada por un error en el procesamiento de OLE. Esta clase la usan los contenedores y los servidores.

[COleDispatchException](reference/coledispatchexception-class.md)<br/>
Excepción resultante de un error durante la automatización. Los servidores de automatización producen las excepciones de automatización y las detectan los clientes de automatización.

[CResourceException](reference/cresourceexception-class.md)<br/>
Excepción que es la causa de un error al cargar un recurso de Windows.

[CUserException](reference/cuserexception-class.md)<br/>
Una excepción utilizada para detener una operación iniciada por el usuario. Normalmente, se ha notificado al usuario del problema antes de que se produzca esta excepción.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
