---
title: Los pasos en una aplicación de cliente de Internet típica | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1c7a7053b8378ea62dc0291dba1b79b794dd099
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="steps-in-a-typical-internet-client-application"></a>Pasos de una aplicación cliente de Internet típica
En la tabla siguiente se muestra los pasos que puede realizar en una aplicación de cliente de Internet típica.  
  
|El objetivo|Acciones que realizar|Efectos|  
|---------------|----------------------|-------------|  
|Comenzar una sesión de Internet.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Inicializa WinInet y se conecta al servidor.|  
|Establecer una opción de consulta de Internet (límite de tiempo de espera o número de reintentos, por ejemplo).|Use [CInternetSession:: SetOption](../mfc/reference/cinternetsession-class.md#setoption).|Devuelve FALSE si la operación tuvo éxito.|  
|Establecer una función de devolución de llamada para supervisar el estado de la sesión.|Use [CInternetSession:: EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback).|Establece una devolución de llamada [CInternetSession:: OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback). Invalidar `OnStatusCallback` para crear su propia rutina de devolución de llamada.|  
|Conectarse a un servidor de Internet, servidor de la intranet o un archivo local.|Use [CInternetSession:: OpenURL](../mfc/reference/cinternetsession-class.md#openurl).|Analiza la dirección URL y abre una conexión con el servidor especificado. Devuelve un [CStdioFile](../mfc/reference/cstdiofile-class.md) (si se pasa `OpenURL` un nombre de archivo local). Éste es el objeto a través del que obtener acceso a los datos recuperados del servidor o del archivo.|  
|Leer el archivo.|Use [CInternetFile:: Read](../mfc/reference/cinternetfile-class.md#read).|Lee el número especificado de bytes usando el búfer proporcionado.|  
|Control de excepciones.|Use la [CInternetException](../mfc/reference/cinternetexception-class.md) clase.|Administra todos los tipos comunes de excepciones de Internet.|  
|Finalizar la sesión de Internet.|Deseche la [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Limpia automáticamente los identificadores de archivos abiertos y conexiones.|  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Requisitos previos para las clases de cliente de Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
