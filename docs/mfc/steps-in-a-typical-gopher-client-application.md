---
title: Pasos de una aplicación cliente gopher típica
ms.date: 11/04/2016
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
ms.openlocfilehash: ca1a09a4a570fd705e726ac5a1124a4cf4ccb329
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279936"
---
# <a name="steps-in-a-typical-gopher-client-application"></a>Pasos de una aplicación cliente gopher típica

En la tabla siguiente muestra los pasos que puede realizar en una aplicación cliente gopher típica.

|El objetivo|Acciones que realizar|Efectos|
|---------------|----------------------|-------------|
|Iniciar una sesión de gopher.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Inicializa WinInet y se conecta al servidor.|
|Conectarse a un servidor gopher.|Use [CInternetSession:: GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection).|Devuelve un [CGopherConnection](../mfc/reference/cgopherconnection-class.md) objeto.|
|Buscar el primer recurso de la red gopher.|Use [CGopherFileFind:: FindFile](../mfc/reference/cgopherfilefind-class.md#findfile).|Busca el primer archivo. Devuelve FALSE si no se encuentran archivos.|
|Buscar el siguiente recurso de la red gopher.|Use [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile).|Busca el archivo siguiente. Devuelve FALSE si no se encuentra el archivo.|
|Abra el archivo se encuentra por `FindFile` o `FindNextFile` para leerlo.|Obtener un localizador gopher mediante [CGopherFileFind:: GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Use [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Se abre el archivo especificado por el localizador. `OpenFile` Devuelve un [CGopherFile](../mfc/reference/cgopherfile-class.md) objeto.|
|Abrir un archivo con un localizador gopher que proporcione.|Crear un localizador gopher mediante [CGopherConnection:: CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator). Use [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Se abre el archivo especificado por el localizador. `OpenFile` Devuelve un [CGopherFile](../mfc/reference/cgopherfile-class.md) objeto.|
|Leer el archivo.|Use [CGopherFile](../mfc/reference/cgopherfile-class.md).|Lee el número especificado de bytes mediante un búfer proporcionado.|
|Control de excepciones.|Use la [CInternetException](../mfc/reference/cinternetexception-class.md) clase.|Controla todos los tipos de excepciones comunes de Internet.|
|Finalizar la sesión de gopher.|Desechar la [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Limpia automáticamente los identificadores de archivos abiertos y las conexiones.|

## <a name="see-also"></a>Vea también

[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
