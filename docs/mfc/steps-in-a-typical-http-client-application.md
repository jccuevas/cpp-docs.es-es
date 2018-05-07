---
title: Los pasos de una aplicación cliente HTTP típica | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTTP client applications [MFC]
- client applications [MFC], HTTP
- Internet applications [MFC], HTTP client applications
- applications [MFC], HTTP client
- Internet client applications [MFC], HTTP table
- WinInet classes [MFC], HTTP
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c25402662296a9ebf2f15fe902dcefabb9d47073
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="steps-in-a-typical-http-client-application"></a>Pasos de una aplicación cliente HTTP típica
En la tabla siguiente se muestra los pasos que puede realizar en una aplicación de cliente HTTP típica:  
  
|El objetivo|Acciones que realizar|Efectos|  
|---------------|----------------------|-------------|  
|Comenzar una sesión HTTP.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Inicializa WinInet y se conecta al servidor.|  
|Conectarse a un servidor HTTP.|Use [CInternetSession:: GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection).|Devuelve un [CHttpConnection](../mfc/reference/chttpconnection-class.md) objeto.|  
|Abra una solicitud HTTP.|Use [CHttpConnection:: OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest).|Devuelve un [CHttpFile](../mfc/reference/chttpfile-class.md) objeto.|  
|Enviar una solicitud HTTP.|Use [CHttpFile:: AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders) y [CHttpFile:: SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|Busca el archivo. Devuelve FALSE si no se encuentra el archivo.|  
|Leer el archivo.|Use [CHttpFile](../mfc/reference/chttpfile-class.md).|Lee el número especificado de bytes usando el búfer proporcionado.|  
|Control de excepciones.|Use la [CInternetException](../mfc/reference/cinternetexception-class.md) clase.|Administra todos los tipos comunes de excepciones de Internet.|  
|Finalizar la sesión HTTP.|Deseche la [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Limpia automáticamente los identificadores de archivos abiertos y conexiones.|  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Requisitos previos para las clases de cliente de Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
