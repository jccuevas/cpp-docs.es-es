---
title: "CGopherFileFind Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CGopherFileFind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherFileFind class"
  - "búsquedas en archivos [C++]"
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CGopherFileFind Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Ayuda en las búsquedas del archivo de Internet de servidores gopher.  
  
> [!NOTE]
>  Se han dejado de utilizar las clases `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros porque no funcionan en la plataforma de Windows XP, pero seguirán funcionando en plataformas anteriores.  
  
## Sintaxis  
  
```  
class CGopherFileFind : public CFileFind  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherFileFind::CGopherFileFind](../Topic/CGopherFileFind::CGopherFileFind.md)|Crea un objeto `CGopherFileFind`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherFileFind::FindFile](../Topic/CGopherFileFind::FindFile.md)|encuentra un archivo en un servidor gopher.|  
|[CGopherFileFind::FindNextFile](../Topic/CGopherFileFind::FindNextFile.md)|continúa una búsqueda de archivos de una llamada anterior a [FindFile](../Topic/CGopherFileFind::FindFile.md).|  
|[CGopherFileFind::GetCreationTime](../Topic/CGopherFileFind::GetCreationTime.md)|Obtiene el tiempo que el archivo especificado se creó.|  
|[CGopherFileFind::GetLastAccessTime](../Topic/CGopherFileFind::GetLastAccessTime.md)|Obtiene el tiempo que el archivo especificado se tuvo acceso en último lugar.|  
|[CGopherFileFind::GetLastWriteTime](../Topic/CGopherFileFind::GetLastWriteTime.md)|Obtiene el tiempo que el archivo especificado se escribió en último lugar en.|  
|[CGopherFileFind::GetLength](../Topic/CGopherFileFind::GetLength.md)|Obtiene la longitud del archivo encontrado, en bytes.|  
|[CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md)|Obtiene un objeto de `CGopherLocator` .|  
|[CGopherFileFind::GetScreenName](../Topic/CGopherFileFind::GetScreenName.md)|obtiene el nombre de una pantalla de gopher.|  
|[CGopherFileFind::IsDots](../Topic/CGopherFileFind::IsDots.md)|Pruebas para marcadores de directorio actual y directorio primario mientras recorre en iteración los archivos.|  
  
## Comentarios  
 `CGopherFileFind` incluye las funciones miembro que inicia una búsqueda, busque un archivo, y devuelve la dirección URL de un archivo.  
  
 Otras clases MFC diseñadas para internet y el archivo local buscar incluyen [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) y [CFileFind](../../mfc/reference/cfilefind-class.md).  Así como `CGopherFileFind`, estas clases proporcionan un mecanismo sin problemas para que el usuario buscar archivos específicos, sin importar el protocolo de servidor, el tipo de archivo, o la ubicación \(un equipo local o servidor remoto\). Observe que no hay ninguna clase MFC para buscar en los servidores HTTP porque el HTTP no admite la manipulación de archivos directa requerida por búsquedas.  
  
> [!NOTE]
>  `CGopherFileFind` no admite las siguientes funciones miembro de su clase base [CFileFind](../../mfc/reference/cfilefind-class.md):  
  
-   [GetRoot](../Topic/CFileFind::GetRoot.md)  
  
-   [GetFileName](../Topic/CFileFind::GetFileName.md)  
  
-   [GetFilePath](../Topic/CFileFind::GetFilePath.md)  
  
-   [GetFileTitle](../Topic/CFileFind::GetFileTitle.md)  
  
-   [GetFileURL](../Topic/CFileFind::GetFileURL.md)  
  
 Además, cuando se utiliza con `CGopherFileFind`, la función [IsDots](../Topic/CFileFind::IsDots.md) miembro de `CFileFind` siempre es **FALSO**.  
  
 Para obtener más información sobre cómo utilizar el `CGopherFileFind` y las clases WinInet, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CGopherFileFind`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CFileFind Class](../../mfc/reference/cfilefind-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind Class](../../mfc/reference/cftpfilefind-class.md)   
 [CFileFind Class](../../mfc/reference/cfilefind-class.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)