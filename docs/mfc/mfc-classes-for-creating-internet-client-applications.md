---
title: Clases MFC para crear aplicaciones cliente de Internet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e2365c0009bee3974cefcb7e9cb77f57045d712
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388745"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>Clases de MFC para crear aplicaciones cliente de Internet

MFC proporciona las siguientes clases y funciones globales para escribir aplicaciones cliente de Internet. Sangría indica que una clase se deriva de la clase alineada por encima de él. `CGopherFile` y `CHttpFile` derivan `CInternetFile`, por ejemplo. Estas clases y funciones globales se declaran en AFXINET. H, excepto `CFileFind`, que se declara en AFX. H.

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

- [CInternetException](../mfc/reference/cinternetexception-class.md)

## <a name="global-functions"></a>Funciones globales

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>Vea también

[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
