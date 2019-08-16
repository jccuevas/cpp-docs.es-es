---
title: Pasos de una aplicación cliente de Internet típica
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
ms.openlocfilehash: 9762e762680e2ac530b87baeac7afdea77ef6f14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306943"
---
# <a name="steps-in-a-typical-internet-client-application"></a>Pasos de una aplicación cliente de Internet típica

En la tabla siguiente muestra los pasos que puede realizar en una aplicación de cliente de Internet típica.

|El objetivo|Acciones que realizar|Efectos|
|---------------|----------------------|-------------|
|Comenzar una sesión de Internet.|Crear un [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Inicializa WinInet y se conecta al servidor.|
|Establecer una opción de consulta de Internet (límite de tiempo de espera o número de reintentos, por ejemplo).|Use [CInternetSession:: SetOption](../mfc/reference/cinternetsession-class.md#setoption).|Devuelve FALSE si la operación tuvo éxito.|
|Establecer una función de devolución de llamada para supervisar el estado de la sesión.|Use [CInternetSession:: EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback).|Establece una devolución de llamada [CInternetSession:: OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback). Invalidar `OnStatusCallback` para crear su propia rutina de devolución de llamada.|
|Conectarse a un servidor de Internet, servidor de la intranet o un archivo local.|Use [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl).|Analiza la dirección URL y abre una conexión al servidor especificado. Devuelve un [CStdioFile](../mfc/reference/cstdiofile-class.md) (si se pasa `OpenURL` un nombre de archivo local). Éste es el objeto a través del cual obtener acceso a datos recuperados del servidor o del archivo.|
|Leer el archivo.|Use [CInternetFile:: Read](../mfc/reference/cinternetfile-class.md#read).|Lee el número especificado de bytes utilizando un búfer proporcionado.|
|Control de excepciones.|Use la [CInternetException](../mfc/reference/cinternetexception-class.md) clase.|Controla todos los tipos de excepciones comunes de Internet.|
|Finalizar la sesión de Internet.|Desechar la [CInternetSession](../mfc/reference/cinternetsession-class.md) objeto.|Limpia automáticamente los identificadores de archivos abiertos y las conexiones.|

## <a name="see-also"></a>Vea también

[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Escritura de una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
