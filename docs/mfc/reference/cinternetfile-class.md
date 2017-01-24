---
title: "CInternetFile Class | Microsoft Docs"
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
  - "CInternetFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInternetFile class"
  - "Internet files"
  - "Internet files, CInternetFile class"
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInternetFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

permite el acceso a los archivos en los sistemas remotos que utilizan protocolos de Internet.  
  
## Sintaxis  
  
```  
  
class CInternetFile : public CStdioFile  
  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetFile::CInternetFile](../Topic/CInternetFile::CInternetFile.md)|Crea un objeto `CInternetFile`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetFile::Abort](../Topic/CInternetFile::Abort.md)|Cierre el archivo, omitiendo todas las advertencias y errores.|  
|[CInternetFile::Close](../Topic/CInternetFile::Close.md)|Cierre `CInternetFile` y libera los recursos.|  
|[CInternetFile::Flush](../Topic/CInternetFile::Flush.md)|Vacía el contenido del búfer de escritura y asegúrese de que los datos en memoria está escrito en el equipo.|  
|[CInternetFile::GetLength](../Topic/CInternetFile::GetLength.md)|Devuelve el tamaño del archivo.|  
|[CInternetFile::Read](../Topic/CInternetFile::Read.md)|lee el número de bytes especificados.|  
|[CInternetFile::ReadString](../Topic/CInternetFile::ReadString.md)|lee una secuencia de caracteres.|  
|[CInternetFile::Seek](../Topic/CInternetFile::Seek.md)|Coloca el puntero de un archivo abierto.|  
|[CInternetFile::SetReadBufferSize](../Topic/CInternetFile::SetReadBufferSize.md)|Establece el tamaño del búfer donde los datos se interpretarán.|  
|[CInternetFile::SetWriteBufferSize](../Topic/CInternetFile::SetWriteBufferSize.md)|Establece el tamaño del búfer donde los datos se escriben.|  
|[CInternetFile::Write](../Topic/CInternetFile::Write.md)|Escriba el número de bytes especificados.|  
|[CInternetFile::WriteString](../Topic/CInternetFile::WriteString.md)|Escribe una cadena terminada en null a un archivo.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetFile::operator HINTERNET](../Topic/CInternetFile::operator%20HINTERNET.md)|Un operador de conversión para un identificador de internet.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetFile::m\_hFile](../Topic/CInternetFile::m_hFile.md)|un identificador a un archivo.|  
  
## Comentarios  
 Proporciona una clase base para las clases del archivo de [CHttpFile](../../mfc/reference/chttpfile-class.md) y de [CGopherFile](../../mfc/reference/cgopherfile-class.md) .  Nunca se crea un objeto de `CInternetFile` directamente.  En su lugar, cree un objeto de una de sus clases derivadas llamando a [CGopherConnection:: OpenFile](../Topic/CGopherConnection::OpenFile.md) o [CHttpConnection:: OpenRequest](../Topic/CHttpConnection::OpenRequest.md).  También puede crear un objeto de `CInternetFile` llamando a [CFtpConnection:: OpenFile](../Topic/CFtpConnection::OpenFile.md).  
  
 Las funciones **Abrir**, `LockRange`, `UnlockRange`, y `Duplicate` miembro de `CInternetFile` no se implementan para `CInternetFile`.  Si llama a estas funciones en un objeto de `CInternetFile` , obtendrá [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Para obtener más información sobre cómo `CInternetFile` funciona con las clases de internet de MFC, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 `CInternetFile`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CStdioFile Class](../../mfc/reference/cstdiofile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)