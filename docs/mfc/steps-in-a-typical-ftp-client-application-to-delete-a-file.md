---
title: "Los pasos de una aplicación cliente FTP típica para eliminar un archivo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 77fecfb9c11c95d14c8816fe1c3b23046eae98c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>Pasos de una aplicación cliente FTP típica para eliminar un archivo
La tabla siguiente muestran los pasos que puede realizar en una aplicación de cliente FTP típica que se elimina un archivo.  
  
|El objetivo|Acciones que realizar|Efectos|  
|---------------|----------------------|-------------|  
|Comenzar una sesión FTP.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Inicializa WinInet y se conecta al servidor.|  
|Conectarse a un servidor FTP.|Use [CInternetSession:: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Devuelve un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objeto.|  
|Compruebe para asegurarse de que se encuentra en el directorio en el servidor FTP.|Use [CFtpConnection:: GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory) o [CFtpConnection:: GetCurrentDirectoryAsURL](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl).|Devuelve el nombre o la dirección URL del directorio que está conectado actualmente en el servidor, dependiendo de la función miembro seleccionado.|  
|Cambiar a un nuevo directorio FTP en el servidor.|Use [CFtpConnection:: SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Cambia el directorio que está conectado actualmente en el servidor.|  
|Buscar el primer archivo en el directorio FTP.|Use [CFtpFileFind:: FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Busca el primer archivo. Devuelve FALSE si no se encuentran archivos.|  
|Buscar el siguiente archivo en el directorio FTP.|Use [CFtpFileFind:: FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Busca el siguiente archivo. Devuelve FALSE si no se encuentra el archivo.|  
|Eliminar el archivo encontrado por **FindFile** o `FindNextFile`.|Use [CFtpConnection:: Remove](../mfc/reference/cftpconnection-class.md#remove), con el nombre de archivo devuelto por **FindFile** o `FindNextFile`.|Elimina el archivo en el servidor para leer o escribir.|  
|Control de excepciones.|Use la [CInternetException](../mfc/reference/cinternetexception-class.md) clase.|Administra todos los tipos comunes de excepciones de Internet.|  
|Finalizar la sesión FTP.|Deseche la [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Limpia automáticamente los identificadores de archivos abiertos y conexiones.|  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Requisitos previos para las clases de cliente de Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
