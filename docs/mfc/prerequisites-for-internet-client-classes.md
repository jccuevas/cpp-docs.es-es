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
ms.openlocfilehash: aaf5756df69728e8ae89fb278bc0671bfc6840b7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619830"
---
# <a name="prerequisites-for-internet-client-classes"></a>Requisitos previos para las clases de cliente Internet

Algunas acciones realizadas por un cliente de Internet (por ejemplo, la lectura de un archivo) tienen acciones de requisitos previos (en este caso, el establecimiento de una conexión a Internet). En las tablas siguientes se enumeran los requisitos previos para algunas acciones de cliente.

### <a name="general-internet-url-ftp-gopher-or-http"></a>Dirección URL general de Internet (FTP, Gopher o HTTP)

|Acción|Requisito previo|
|------------|------------------|
|Establezca una conexión.|Cree un [CInternetSession](reference/cinternetsession-class.md) para establecer la base de una aplicación cliente de Internet.|
|Abra una dirección URL.|Establezca una conexión. Llame a [CInternetSession:: OpenURL](reference/cinternetsession-class.md#openurl). La `OpenURL` función devuelve un objeto de recurso de solo lectura.|
|Leer los datos de la dirección URL.|Abra la dirección URL. Llame a [CInternetFile:: Read](reference/cinternetfile-class.md#read).|
|Establezca una opción de Internet.|Establezca una conexión. Llame a [CInternetSession:: SetOption](reference/cinternetsession-class.md#setoption).|
|Establezca una función a la que se llamará con información de estado.|Establezca una conexión. Llame a [CInternetSession:: EnableStatusCallback](reference/cinternetsession-class.md#enablestatuscallback). Invalide [CInternetSession:: OnStatusCallback](reference/cinternetsession-class.md#onstatuscallback) para controlar las llamadas.|

### <a name="ftp"></a>FTP

|Acción|Requisito previo|
|------------|------------------|
|Establezca una conexión FTP.|Cree un [CInternetSession](reference/cinternetsession-class.md) como base de esta aplicación cliente de Internet. Llame a [CInternetSession:: GetFtpConnection](reference/cinternetsession-class.md#getftpconnection) para crear un objeto [CFtpConnection](reference/cftpconnection-class.md) .|
|Busque el primer recurso.|Establezca una conexión FTP. Cree un objeto [CFtpFileFind](reference/cftpfilefind-class.md) . Llame a [CFtpFileFind:: findfile](reference/cftpfilefind-class.md#findfile).|
|Enumerar todos los recursos disponibles.|Busque el primer archivo. Llame a [CFtpFileFind:: FindNextFile](reference/cftpfilefind-class.md#findnextfile) hasta que devuelva false.|
|Abra un archivo FTP.|Establezca una conexión FTP. Llame a [CFtpConnection:: OpenFile](reference/cftpconnection-class.md#openfile) para crear y abrir un objeto [CInternetFile](reference/cinternetfile-class.md) .|
|Leer un archivo FTP.|Abra un archivo FTP con acceso de lectura. Llame a [CInternetFile:: Read](reference/cinternetfile-class.md#read).|
|Escribir en un archivo FTP.|Abra un archivo FTP con acceso de escritura. Llame a [CInternetFile:: Write](reference/cinternetfile-class.md#write).|
|Cambie el directorio del cliente en el servidor.|Establezca una conexión FTP. Llame a [CFtpConnection:: SetCurrentDirectory](reference/cftpconnection-class.md#setcurrentdirectory).|
|Recupere el directorio actual del cliente en el servidor.|Establezca una conexión FTP. Llame a [CFtpConnection:: GetCurrentDirectory](reference/cftpconnection-class.md#getcurrentdirectory).|

### <a name="http"></a>HTTP

|Acción|Requisito previo|
|------------|------------------|
|Establezca una conexión HTTP.|Cree un [CInternetSession](reference/cinternetsession-class.md) como base de esta aplicación cliente de Internet. Llame a [CInternetSession:: GetHttpConnection](reference/cinternetsession-class.md#gethttpconnection) para crear un objeto [CHttpConnection (](reference/chttpconnection-class.md) .|
|Abra un archivo HTTP.|Establezca una conexión HTTP. Llame a [CHttpConnection (:: OpenRequest](reference/chttpconnection-class.md#openrequest) para crear un objeto [CHttpFile](reference/chttpfile-class.md) . Llame a [CHttpFile:: AddRequestHeaders](reference/chttpfile-class.md#addrequestheaders). Llame a [CHttpFile:: SendRequest](reference/chttpfile-class.md#sendrequest).|
|Leer un archivo HTTP.|Abra un archivo HTTP. Llame a [CInternetFile:: Read](reference/cinternetfile-class.md#read).|
|Obtener información acerca de una solicitud HTTP.|Establezca una conexión HTTP. Llame a [CHttpConnection (:: OpenRequest](reference/chttpconnection-class.md#openrequest) para crear un objeto [CHttpFile](reference/chttpfile-class.md) . Llame a [CHttpFile:: QueryInfo](reference/chttpfile-class.md#queryinfo).|

### <a name="gopher"></a>:/

|Acción|Requisito previo|
|------------|------------------|
|Establezca una conexión Gopher.|Cree un [CInternetSession](reference/cinternetsession-class.md) como base de esta aplicación cliente de Internet. Llame a [CInternetSession:: GetGopherConnection](reference/cinternetsession-class.md#getgopherconnection) para crear un [CGopherConnection](reference/cgopherconnection-class.md).|
|Busca el primer archivo en el directorio actual.|Establezca una conexión Gopher. Cree un objeto [CGopherFileFind](reference/cgopherfilefind-class.md) . Llame a [CGopherConnection:: CreateLocator](reference/cgopherconnection-class.md#createlocator) para crear un objeto [CGopherLocator](reference/cgopherlocator-class.md) . Pase el localizador a [CGopherFileFind:: findfile](reference/cgopherfilefind-class.md#findfile). Llame a [CGopherFileFind:: GetLocator](reference/cgopherfilefind-class.md#getlocator) para obtener el localizador de un archivo si lo necesita más adelante.|
|Enumerar todos los archivos disponibles.|Busque el primer archivo. Llame a [CGopherFileFind:: FindNextFile](reference/cgopherfilefind-class.md#findnextfile) hasta que devuelva false.|
|Abra un archivo Gopher.|Establezca una conexión Gopher. Cree un localizador de Gopher con [CGopherConnection:: CreateLocator](reference/cgopherconnection-class.md#createlocator) o busque un localizador con [CGopherFileFind:: GetLocator](reference/cgopherfilefind-class.md#getlocator). Llame a [CGopherConnection:: OpenFile](reference/cgopherconnection-class.md#openfile).|
|Lea un archivo Gopher.|Abra un archivo Gopher. Use [CGopherFile (](reference/cgopherfile-class.md).|

## <a name="see-also"></a>Consulte también

[Extensiones de Internet Win32 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Clases de MFC para crear aplicaciones cliente de Internet](mfc-classes-for-creating-internet-client-applications.md)<br/>
[Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](writing-an-internet-client-application-using-mfc-wininet-classes.md)
