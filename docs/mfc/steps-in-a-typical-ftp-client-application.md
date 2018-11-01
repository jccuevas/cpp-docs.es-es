---
title: Los pasos de una aplicación cliente FTP típica | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ac1eef12a3f782f3ad9ba8a9bb526989876251e
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890223"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>Pasos de una aplicación cliente FTP típica

Crea una aplicación de cliente FTP típica un [CInternetSession](../mfc/reference/cinternetsession-class.md) y un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objeto. Tenga en cuenta que estas clases WinInet de MFC no controlar realmente la configuración del tipo de proxy; IIS proporciona.

En la tabla siguiente muestra los pasos que puede realizar en una aplicación de cliente FTP típica.

|El objetivo|Acciones que realizar|Efectos|
|---------------|----------------------|-------------|
|Comenzar una sesión FTP.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Inicializa WinInet y se conecta al servidor.|
|Conectarse a un servidor FTP.|Use [CInternetSession:: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Devuelve un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objeto.|
|Cambiar a un nuevo directorio FTP en el servidor.|Use [CFtpConnection:: SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Cambia el directorio que está conectado actualmente en el servidor.|
|Buscar el primer archivo en el directorio FTP.|Use [CFtpFileFind:: FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Busca el primer archivo. Devuelve FALSE si no se encuentran archivos.|
|El siguiente archivo de búsqueda en el directorio FTP.|Use [CFtpFileFind:: FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Busca el archivo siguiente. Devuelve FALSE si no se encuentra el archivo.|
|Abra el archivo se encuentra por `FindFile` o `FindNextFile` para lectura o escritura.|Use [CFtpConnection:: OpenFile](../mfc/reference/cftpconnection-class.md#openfile), con el nombre de archivo devuelta por [FindFile](../mfc/reference/cftpfilefind-class.md#findfile) o [FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Abre el archivo en el servidor de lectura o escritura. Devuelve un [CInternetFile](../mfc/reference/cinternetfile-class.md) objeto.|
|Leer o escribir en el archivo.|Use [CInternetFile:: Read](../mfc/reference/cinternetfile-class.md#read) o [CInternetFile:: Write](../mfc/reference/cinternetfile-class.md#write).|Lee o escribe el número especificado de bytes mediante un búfer proporcionado.|
|Control de excepciones.|Use la [CInternetException](../mfc/reference/cinternetexception-class.md) clase.|Controla todos los tipos de excepciones comunes de Internet.|
|Finalizar la sesión FTP.|Desechar la [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Limpia automáticamente los identificadores de archivos abiertos y las conexiones.|

## <a name="see-also"></a>Vea también

[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
