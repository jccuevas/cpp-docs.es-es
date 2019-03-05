---
title: Requisitos previos para las clases de cliente Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Internet files [MFC], writing to
- Internet [MFC], connections
- FTP (File Transfer Protocol), MFC classes
- Gopher prerequisites [MFC]
- files [MFC], writing to
- classes [MFC], connections
- HTTP [MFC], prerequisites for Internet clients
- connections [MFC], classes for
- Internet client class prerequisites [MFC]
- files [MFC], reading
- URLs [MFC], Internet client applications
- prerequisites, Internet client classes [MFC]
- Gopher client applications [MFC]
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
ms.openlocfilehash: 6246db7dfb2837f5d94fa51f8433b46722c43663
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267750"
---
# <a name="prerequisites-for-internet-client-classes"></a>Requisitos previos para las clases de cliente Internet

Algunas acciones realizadas por un cliente de Internet (lectura de un archivo, por ejemplo) tiene acciones de requisitos previos (en este caso, establecer una conexión a Internet). Las siguientes tablas enumeran los requisitos previos para algunas acciones de cliente.

### <a name="general-internet-url-ftp-gopher-or-http"></a>Dirección URL de Internet general (FTP, Gopher o HTTP)

|Acción|Requisito previo|
|------------|------------------|
|Establecer una conexión.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) para establecer la base de una aplicación de cliente de Internet.|
|Abra una dirección URL.|Establecer una conexión. Call [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl). El `OpenURL` función devuelve un objeto de recurso de solo lectura.|
|Datos de la dirección URL de lectura.|Abra la dirección URL. Llame a [CInternetFile:: Read](../mfc/reference/cinternetfile-class.md#read).|
|Establecer una opción de Internet.|Establecer una conexión. Llame a [CInternetSession:: SetOption](../mfc/reference/cinternetsession-class.md#setoption).|
|Establece una función que se llamará con información de estado.|Establecer una conexión. Llame a [CInternetSession:: EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback). Invalidar [CInternetSession:: OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) para controlar las llamadas.|

### <a name="ftp"></a>FTP

|Acción|Requisito previo|
|------------|------------------|
|Establecer una conexión FTP.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) como base de esta aplicación de cliente de Internet. Llame a [CInternetSession:: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection) para crear un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objeto.|
|Buscar el primer recurso.|Establecer una conexión FTP. Crear un [CFtpFileFind](../mfc/reference/cftpfilefind-class.md) objeto. Llame a [CFtpFileFind:: FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|
|Enumerar todos los recursos disponibles.|Buscar el primer archivo. Llame a [CFtpFileFind:: FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile) hasta que devuelva FALSE.|
|Abra un archivo FTP.|Establecer una conexión FTP. Llame a [CFtpConnection:: OpenFile](../mfc/reference/cftpconnection-class.md#openfile) para crear y abrir un [CInternetFile](../mfc/reference/cinternetfile-class.md) objeto.|
|Leer un archivo FTP.|Abrir un archivo FTP con acceso de lectura. Llame a [CInternetFile:: Read](../mfc/reference/cinternetfile-class.md#read).|
|Escribir en un archivo FTP.|Abrir un archivo FTP con acceso de escritura. Llame a [CInternetFile:: Write](../mfc/reference/cinternetfile-class.md#write).|
|Cambie el directorio del cliente en el servidor.|Establecer una conexión FTP. Llame a [CFtpConnection:: SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|
|Recuperar el directorio actual del cliente en el servidor.|Establecer una conexión FTP. Llame a [CFtpConnection:: GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory).|

### <a name="http"></a>HTTP

|Acción|Requisito previo|
|------------|------------------|
|Establecer una conexión HTTP.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) como base de esta aplicación de cliente de Internet. Llame a [CInternetSession:: GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection) para crear un [CHttpConnection](../mfc/reference/chttpconnection-class.md) objeto.|
|Abra un archivo HTTP.|Establecer una conexión HTTP. Llame a [CHttpConnection:: OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest) para crear un [CHttpFile](../mfc/reference/chttpfile-class.md) objeto. Llame a [CHttpFile:: AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders). Llame a [CHttpFile:: SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|
|Leer un archivo HTTP.|Abra un archivo HTTP. Llame a [CInternetFile:: Read](../mfc/reference/cinternetfile-class.md#read).|
|Obtenga información sobre una solicitud HTTP.|Establecer una conexión HTTP. Llame a [CHttpConnection:: OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest) para crear un [CHttpFile](../mfc/reference/chttpfile-class.md) objeto. Llame a [QueryInfo](../mfc/reference/chttpfile-class.md#queryinfo).|

### <a name="gopher"></a>Gopher

|Acción|Requisito previo|
|------------|------------------|
|Establecer una conexión gopher.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) como base de esta aplicación de cliente de Internet. Llame a [CInternetSession:: GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection) para crear un [CGopherConnection](../mfc/reference/cgopherconnection-class.md).|
|Buscar el primer archivo en el directorio actual.|Establecer una conexión gopher. Crear un [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md) objeto. Llame a [CGopherConnection:: CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator) para crear un [CGopherLocator](../mfc/reference/cgopherlocator-class.md) objeto. Pasar el localizador [CGopherFileFind:: FindFile](../mfc/reference/cgopherfilefind-class.md#findfile). Llame a [CGopherFileFind:: GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator) para obtener el localizador de un archivo si lo necesitará más adelante.|
|Enumerar todos los archivos disponibles.|Buscar el primer archivo. Llame a [CGopherFileFind:: FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile) hasta que devuelva FALSE.|
|Abra un archivo gopher.|Establecer una conexión gopher. Crear un localizador gopher con [CGopherConnection:: CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator) o buscar un localizador con [CGopherFileFind:: GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Call [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|
|Leer un archivo gopher.|Abra un archivo gopher. Use [CGopherFile](../mfc/reference/cgopherfile-class.md).|

## <a name="see-also"></a>Vea también

[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Clases MFC para crear aplicaciones cliente de Internet](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
