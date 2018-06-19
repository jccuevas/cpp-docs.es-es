---
title: Los pasos de una aplicación cliente FTP típica | Documentos de Microsoft
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
ms.openlocfilehash: 98f5a21bd5fa20a40123ce442959125ea62c60d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381129"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>Pasos de una aplicación cliente FTP típica
Crea una aplicación de cliente FTP típica un [CInternetSession](../mfc/reference/cinternetsession-class.md) y un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objeto. Tenga en cuenta que estas clases WinInet de MFC no controlan en realidad la configuración del tipo de proxy; IIS realiza.  
  
 Además, vea estos artículos de Knowledge Base:  
  
-   Cómo: FTP con Proxy basado en CERN con la API WinInet (Id. de artículo: Q166961)  
  
-   EJEMPLO: FTP con contraseñas locales basados en CERN protegido Proxy (Id. de artículo: Q216214)  
  
-   Se produce un error de administrador para mostrar los servicios de Proxy instalado servicios de Internet (Id. de artículo: Q216802)  
  
 En la tabla siguiente se muestra los pasos que puede realizar en una aplicación de cliente FTP típica.  
  
|El objetivo|Acciones que realizar|Efectos|  
|---------------|----------------------|-------------|  
|Comenzar una sesión FTP.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Inicializa WinInet y se conecta al servidor.|  
|Conectarse a un servidor FTP.|Use [CInternetSession:: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Devuelve un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objeto.|  
|Cambiar a un nuevo directorio FTP en el servidor.|Use [CFtpConnection:: SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Cambia el directorio que está conectado actualmente en el servidor.|  
|Buscar el primer archivo en el directorio FTP.|Use [CFtpFileFind:: FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Busca el primer archivo. Devuelve FALSE si no se encuentran archivos.|  
|Buscar el siguiente archivo en el directorio FTP.|Use [CFtpFileFind:: FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Busca el siguiente archivo. Devuelve FALSE si no se encuentra el archivo.|  
|Abra el archivo encontrado por **FindFile** o `FindNextFile` para leer o escribir.|Use [CFtpConnection:: OpenFile](../mfc/reference/cftpconnection-class.md#openfile), con el nombre de archivo devuelto por [FindFile](../mfc/reference/cftpfilefind-class.md#findfile) o [FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Abre el archivo en el servidor para leer o escribir. Devuelve un [CInternetFile](../mfc/reference/cinternetfile-class.md) objeto.|  
|Leer o escribir en el archivo.|Use [CInternetFile:: Read](../mfc/reference/cinternetfile-class.md#read) o [CInternetFile:: Write](../mfc/reference/cinternetfile-class.md#write).|Lee o escribe el número especificado de bytes, con un búfer proporcionado.|  
|Control de excepciones.|Use la [CInternetException](../mfc/reference/cinternetexception-class.md) clase.|Administra todos los tipos comunes de excepciones de Internet.|  
|Finalizar la sesión FTP.|Deseche la [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Limpia automáticamente los identificadores de archivos abiertos y conexiones.|  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Requisitos previos para las clases de cliente de Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
