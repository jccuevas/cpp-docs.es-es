---
title: "Los pasos en una aplicación de cliente Gopher típica | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: de0ea34305b91a30ab545162134d169b198f25d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="steps-in-a-typical-gopher-client-application"></a>Pasos de una aplicación cliente gopher típica
En la tabla siguiente se muestra los pasos que puede realizar en una aplicación de cliente gopher típica.  
  
|El objetivo|Acciones que realizar|Efectos|  
|---------------|----------------------|-------------|  
|Iniciar una sesión de gopher.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Inicializa WinInet y se conecta al servidor.|  
|Conectarse a un servidor gopher.|Use [CInternetSession:: GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection).|Devuelve un [objeto CGopherConnection](../mfc/reference/cgopherconnection-class.md) objeto.|  
|Buscar el primer recurso de la red gopher.|Use [CGopherFileFind:: FindFile](../mfc/reference/cgopherfilefind-class.md#findfile).|Busca el primer archivo. Devuelve FALSE si no se encuentran archivos.|  
|Buscar el siguiente recurso de la red gopher.|Use [CGopherFileFind:: FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile).|Busca el siguiente archivo. Devuelve FALSE si no se encuentra el archivo.|  
|Abra el archivo encontrado por **FindFile** o `FindNextFile` para su lectura.|Obtener un localizador gopher mediante [CGopherFileFind:: GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Use [CGopherConnection:: OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Se abre el archivo especificado por el localizador. `OpenFile`Devuelve un [CGopherFile](../mfc/reference/cgopherfile-class.md) objeto.|  
|Abrir un archivo mediante un localizador gopher que proporcione.|Crear un localizador gopher mediante [CGopherConnection:: CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator). Use [CGopherConnection:: OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Se abre el archivo especificado por el localizador. `OpenFile`Devuelve un [CGopherFile](../mfc/reference/cgopherfile-class.md) objeto.|  
|Leer el archivo.|Use [CGopherFile](../mfc/reference/cgopherfile-class.md).|Lee el número especificado de bytes, con un búfer proporcionado.|  
|Control de excepciones.|Use la [CInternetException](../mfc/reference/cinternetexception-class.md) clase.|Administra todos los tipos comunes de excepciones de Internet.|  
|Finalizar la sesión de gopher.|Deseche la [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Limpia automáticamente los identificadores de archivos abiertos y conexiones.|  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Requisitos previos para las clases de cliente de Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
