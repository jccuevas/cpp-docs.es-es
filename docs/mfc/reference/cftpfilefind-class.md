---
title: "CFtpFileFind Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFtpFileFind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFtpFileFind class"
  - "búsquedas en archivos [C++]"
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
caps.latest.revision: 23
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFtpFileFind Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Ayuda en las búsquedas del archivo de Internet de servidores FTP.  
  
## Sintaxis  
  
```  
class CFtpFileFind : public CFileFind  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFtpFileFind::CFtpFileFind](../Topic/CFtpFileFind::CFtpFileFind.md)|Crea un objeto `CFtpFileFind`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md)|encuentra un archivo en un servidor FTP.|  
|[CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md)|continúa una búsqueda de archivos de una llamada anterior a [FindFile](../Topic/CFtpFileFind::FindFile.md).|  
|[CFtpFileFind::GetFileURL](../Topic/CFtpFileFind::GetFileURL.md)|Obtiene la dirección URL, incluida la ruta de acceso, el archivo encontrado.|  
  
## Comentarios  
 `CFtpFileFind` incluye las funciones miembro que inicia una búsqueda, busque un archivo, y devuelve la dirección URL u otra información descriptiva sobre el archivo.  
  
 Otras clases MFC diseñadas para internet y el archivo local buscar incluyen [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) y [CFileFind](../../mfc/reference/cfilefind-class.md).  Así como `CFtpFileFind`, estas clases proporcionan un mecanismo sin problemas para que el cliente buscar archivos específicos, sin importar el protocolo o tipo de archivo \(un equipo local o un servidor remoto\) del servidor.  Observe que no hay ninguna clase MFC para buscar en los servidores HTTP porque el HTTP no admite la manipulación de archivos directa requerida para las búsquedas.  
  
 Para obtener más información sobre cómo utilizar el `CFtpFileFind` y las clases WinInet, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## Ejemplo  
 El código siguiente muestra cómo enumerar todos los archivos del directorio actual del servidor FTP.  
  
 [!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/CPP/cftpfilefind-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CFtpFileFind`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CFileFind Class](../../mfc/reference/cfilefind-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)