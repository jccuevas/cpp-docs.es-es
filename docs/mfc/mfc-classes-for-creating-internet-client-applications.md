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
ms.openlocfilehash: d65a2e8b373f26fe928e4c3e7c0193aec4edf2d6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618033"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>Clases de MFC para crear aplicaciones cliente de Internet

MFC proporciona las siguientes clases y funciones globales para escribir aplicaciones cliente de Internet. La sangría indica que una clase se deriva de la clase sin sangría que está sobre ella. `CGopherFile`y `CHttpFile` derivan de `CInternetFile` , por ejemplo. Estas clases y funciones globales se declaran en AFXINET. H, excepto `CFileFind` , que se declara en AFX. C.

## <a name="classes"></a>Clases

- [CInternetSession](reference/cinternetsession-class.md)

- [CInternetConnection](reference/cinternetconnection-class.md)

  - [CFtpConnection](reference/cftpconnection-class.md)

  - [CGopherConnection](reference/cgopherconnection-class.md)

  - [CHttpConnection](reference/chttpconnection-class.md)

- [CInternetFile](reference/cinternetfile-class.md)

  - [CGopherFile](reference/cgopherfile-class.md)

  - [CHttpFile](reference/chttpfile-class.md)

- [CFileFind](reference/cfilefind-class.md)

  - [CFtpFileFind](reference/cftpfilefind-class.md)

  - [CGopherFileFind](reference/cgopherfilefind-class.md)

- [CGopherLocator](reference/cgopherlocator-class.md)

- [Clase CInternetException](reference/cinternetexception-class.md)

## <a name="global-functions"></a>Funciones globales

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>Consulte también

[Extensiones de Internet Win32 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Requisitos previos para las clases de cliente Internet](prerequisites-for-internet-client-classes.md)<br/>
[Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](writing-an-internet-client-application-using-mfc-wininet-classes.md)
