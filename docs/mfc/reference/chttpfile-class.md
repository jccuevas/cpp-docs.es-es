---
title: "CHttpFile Class | Microsoft Docs"
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
  - "CHttpFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHttpFile class"
  - "HTTP (archivos)"
  - "HTTP requests, requesting and reading files"
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
caps.latest.revision: 23
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHttpFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad para aplicar y para leer archivos en un servidor HTTP.  
  
## Sintaxis  
  
```  
class CHttpFile : public CInternetFile  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHttpFile::CHttpFile](../Topic/CHttpFile::CHttpFile.md)|Crea un objeto `CHttpFile`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHttpFile::AddRequestHeaders](../Topic/CHttpFile::AddRequestHeaders.md)|Agrega encabezados a la solicitud enviada a un servidor HTTP.|  
|[CHttpFile::EndRequest](../Topic/CHttpFile::EndRequest.md)|Finaliza una solicitud enviada a un servidor HTTP mediante la función miembro de [SendRequestEx](../Topic/CHttpFile::SendRequestEx.md) .|  
|[CHttpFile::GetFileURL](../Topic/CHttpFile::GetFileURL.md)|Obtiene la dirección URL del archivo especificado.|  
|[CHttpFile::GetObject](../Topic/CHttpFile::GetObject.md)|Obtiene el objeto de destino del verbo en una solicitud a un servidor HTTP.|  
|[CHttpFile::GetVerb](../Topic/CHttpFile::GetVerb.md)|Obtiene el verbo utilizado en una solicitud a un servidor HTTP.|  
|[CHttpFile::QueryInfo](../Topic/CHttpFile::QueryInfo.md)|Devuelve la respuesta o los encabezados de solicitud de servidor HTTP.|  
|[CHttpFile::QueryInfoStatusCode](../Topic/CHttpFile::QueryInfoStatusCode.md)|Recupera el código de estado asociado a una solicitud HTTP y los coloca en el parámetro proporcionado de `dwStatusCode` .|  
|[CHttpFile::SendRequest](../Topic/CHttpFile::SendRequest.md)|Envía una solicitud a un servidor HTTP.|  
|[CHttpFile::SendRequestEx](../Topic/CHttpFile::SendRequestEx.md)|Envía una solicitud a un servidor HTTP mediante [escritura](../Topic/CInternetFile::Write.md) o métodos de [WriteString](../Topic/CInternetFile::WriteString.md) de `CInternetFile`.|  
  
## Comentarios  
 Si su sesión de internet lee datos de un servidor HTTP, debe crear una instancia de `CHttpFile`.  
  
 Para obtener más información sobre cómo `CHttpFile` funciona con las clases de internet de MFC, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CHttpFile`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpConnection Class](../../mfc/reference/chttpconnection-class.md)