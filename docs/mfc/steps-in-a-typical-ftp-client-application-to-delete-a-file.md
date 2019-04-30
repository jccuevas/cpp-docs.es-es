---
title: Pasos de una aplicación cliente FTP típica para eliminar un archivo
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
ms.openlocfilehash: 6d2a920d3053a920638dd20a23e1c2334745bbc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307060"
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>Pasos de una aplicación cliente FTP típica para eliminar un archivo

La siguiente tabla muestra los pasos que puede realizar en una aplicación cliente FTP típica que se elimina un archivo.

|El objetivo|Acciones que realizar|Efectos|
|---------------|----------------------|-------------|
|Comenzar una sesión FTP.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Inicializa WinInet y se conecta al servidor.|
|Conectarse a un servidor FTP.|Use [CInternetSession:: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Devuelve un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objeto.|
|Compruebe que se encuentra en el directorio correcto en el servidor FTP.|Use [CFtpConnection:: GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory) o [CFtpConnection:: GetCurrentDirectoryAsURL](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl).|Devuelve el nombre o la dirección URL del directorio que está conectado actualmente en el servidor, dependiendo de la función miembro seleccionado.|
|Cambiar a un nuevo directorio FTP en el servidor.|Use [CFtpConnection:: SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Cambia el directorio que está conectado actualmente en el servidor.|
|Buscar el primer archivo en el directorio FTP.|Use [CFtpFileFind:: FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Busca el primer archivo. Devuelve FALSE si no se encuentran archivos.|
|El siguiente archivo de búsqueda en el directorio FTP.|Use [CFtpFileFind:: FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Busca el archivo siguiente. Devuelve FALSE si no se encuentra el archivo.|
|Eliminar el archivo encontrado por `FindFile` o `FindNextFile`.|Use [CFtpConnection:: Remove](../mfc/reference/cftpconnection-class.md#remove), con el nombre de archivo devuelta por `FindFile` o `FindNextFile`.|Elimina el archivo en el servidor de lectura o escritura.|
|Control de excepciones.|Use la [CInternetException](../mfc/reference/cinternetexception-class.md) clase.|Controla todos los tipos de excepciones comunes de Internet.|
|Finalizar la sesión FTP.|Desechar la [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Limpia automáticamente los identificadores de archivos abiertos y las conexiones.|

## <a name="see-also"></a>Vea también

[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
