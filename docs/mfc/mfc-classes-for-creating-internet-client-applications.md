---
title: Clases de MFC para crear aplicaciones cliente de Internet
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
ms.openlocfilehash: 578fd5b72e6c04610aa862f1a6631895a32a9bfe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358213"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>Clases de MFC para crear aplicaciones cliente de Internet

MFC proporciona las siguientes clases y funciones globales para escribir aplicaciones cliente de Internet. La sangría indica que una clase se deriva de la clase sin sangría por encima de ella. `CGopherFile`y `CHttpFile` derivan `CInternetFile`de , por ejemplo. Estas clases y funciones globales se declaran en AFXINET. H, `CFileFind`excepto , que se declara en AFX. H.

## <a name="classes"></a>Clases

- [CInternetSession](../mfc/reference/cinternetsession-class.md)

- [CInternetConnection](../mfc/reference/cinternetconnection-class.md)

  - [CFtpConnection](../mfc/reference/cftpconnection-class.md)

  - [CGopherConnection](../mfc/reference/cgopherconnection-class.md)

  - [CHttpConnection](../mfc/reference/chttpconnection-class.md)

- [CInternetFile](../mfc/reference/cinternetfile-class.md)

  - [CGopherFile](../mfc/reference/cgopherfile-class.md)

  - [CHttpFile](../mfc/reference/chttpfile-class.md)

- [CFileFind](../mfc/reference/cfilefind-class.md)

  - [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)

  - [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)

- [CGopherLocator](../mfc/reference/cgopherlocator-class.md)

- [Clase CInternetException](../mfc/reference/cinternetexception-class.md)

## <a name="global-functions"></a>Funciones globales

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>Consulte también

[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
