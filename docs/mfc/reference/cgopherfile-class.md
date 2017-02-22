---
title: "CGopherFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CGopherFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherFile (clase)"
  - "gopher protocol files"
  - "Internet, gopher"
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CGopherFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad para buscar y leer los archivos en un servidor gopher.  
  
> [!NOTE]
>  Se han dejado de utilizar las clases `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros porque no funcionan en la plataforma de Windows XP, pero seguirán funcionando en plataformas anteriores.  
  
## Sintaxis  
  
```  
class CGopherFile : public CInternetFile  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherFile::CGopherFile](../Topic/CGopherFile::CGopherFile.md)|Crea un objeto `CGopherFile`.|  
  
## Comentarios  
 El servicio de gopher no permite que los usuarios escriban datos a un archivo de gopher porque las funciones de este servicio principalmente como interfaz controlada por menú para buscar información.  Las funciones **Write**, `WriteString`, y `Flush` miembro de `CGopherFile` no se implementan para `CGopherFile`.  Llamando a estas funciones en `CGopherFile` opóngase, retornos [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Para obtener más información sobre cómo `CGopherFile` funciona con las clases de internet de MFC, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherLocator Class](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection Class](../../mfc/reference/cgopherconnection-class.md)