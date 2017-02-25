---
title: "CFileFind Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFileFind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileFind class"
  - "archivos [C++], buscar"
  - "Internet files [C++], buscar"
  - "local files"
  - "local files, buscar"
  - "URLs [C++], buscar"
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CFileFind Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza búsquedas de archivos locales y es la clase base para [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) y [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), que realizan búsquedas del archivo de Internet.  
  
## Sintaxis  
  
```  
class CFileFind : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileFind::CFileFind](../Topic/CFileFind::CFileFind.md)|Crea un objeto `CFileFind`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileFind::Close](../Topic/CFileFind::Close.md)|Cierra la solicitud de búsqueda.|  
|[CFileFind::FindFile](../Topic/CFileFind::FindFile.md)|busca un directorio para un nombre de archivo especificado.|  
|[CFileFind::FindNextFile](../Topic/CFileFind::FindNextFile.md)|continúa una búsqueda de archivos de una llamada anterior a [FindFile](../Topic/CFileFind::FindFile.md).|  
|[CFileFind::GetCreationTime](../Topic/CFileFind::GetCreationTime.md)|Obtiene el tiempo que el archivo se creó.|  
|[CFileFind::GetFileName](../Topic/CFileFind::GetFileName.md)|Obtiene el nombre, incluida la extensión, el archivo encontrado|  
|[CFileFind::GetFilePath](../Topic/CFileFind::GetFilePath.md)|Obtiene la ruta de acceso completa del archivo encontrado.|  
|[CFileFind::GetFileTitle](../Topic/CFileFind::GetFileTitle.md)|Obtiene el título del archivo encontrado.  El título no incluye la extensión.|  
|[CFileFind::GetFileURL](../Topic/CFileFind::GetFileURL.md)|Obtiene la dirección URL, incluida la ruta de acceso, el archivo encontrado.|  
|[CFileFind::GetLastAccessTime](../Topic/CFileFind::GetLastAccessTime.md)|Obtiene el tiempo que se acceso en último lugar.|  
|[CFileFind::GetLastWriteTime](../Topic/CFileFind::GetLastWriteTime.md)|Obtiene el tiempo que el archivo se ha cambiado y que guardado por última vez.|  
|[CFileFind::GetLength](../Topic/CFileFind::GetLength.md)|Obtiene la longitud del archivo encontrado, en bytes.|  
|[CFileFind::GetRoot](../Topic/CFileFind::GetRoot.md)|Obtiene el directorio raíz del archivo encontrado.|  
|[CFileFind::IsArchived](../Topic/CFileFind::IsArchived.md)|determina si se almacena el archivo encontrado.|  
|[CFileFind::IsCompressed](../Topic/CFileFind::IsCompressed.md)|determina si el archivo encontrado es cifrado.|  
|[CFileFind::IsDirectory](../Topic/CFileFind::IsDirectory.md)|determina si el archivo encontrado es un directorio.|  
|[CFileFind::IsDots](../Topic/CFileFind::IsDots.md)|Determina si el nombre del archivo situado tiene el nombre “.” o “. ”, que indica que es realmente un directorio.|  
|[CFileFind::IsHidden](../Topic/CFileFind::IsHidden.md)|Determina si el archivo está oculto encontrado.|  
|[CFileFind::IsNormal](../Topic/CFileFind::IsNormal.md)|determina si el archivo encontrado es normal \(es decir no tiene ningún otro atributo\).|  
|[CFileFind::IsReadOnly](../Topic/CFileFind::IsReadOnly.md)|Determina si el archivo encontrado es de solo lectura.|  
|[CFileFind::IsSystem](../Topic/CFileFind::IsSystem.md)|determina si el archivo encontrado es un archivo de sistema.|  
|[CFileFind::IsTemporary](../Topic/CFileFind::IsTemporary.md)|determina si el archivo encontrado es temporal.|  
|[CFileFind::MatchesMask](../Topic/CFileFind::MatchesMask.md)|Indica los atributos de archivo deseados del archivo que se buscará.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileFind::CloseContext](../Topic/CFileFind::CloseContext.md)|Cierre el archivo especificado por el identificador de búsqueda actual.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileFind::m\_pTM](../Topic/CFileFind::m_pTM.md)|puntero a un objeto de `CAtlTransactionManager` .|  
  
## Comentarios  
 `CFileFind` incluye las funciones miembro que inicia una búsqueda, busque un archivo, y devuelven el título, el nombre, o la ruta de acceso del archivo.  Para las búsquedas de internet, la función [GetFileURL](../Topic/CFileFind::GetFileURL.md) miembro devuelve la dirección URL del archivo.  
  
 `CFileFind` es la clase base para otras dos clases MFC diseñadas para buscar tipos de servidor concretos: `CGopherFileFind` funciona específicamente con los servidores gopher, y `CFtpFileFind` funciona específicamente con los servidores FTP.  Juntas, estas tres clases proporcionan un mecanismo sin problemas para que el cliente buscar archivos, independientemente del protocolo de servidor, el tipo de archivo, o la ubicación, en un equipo local o un servidor remoto.  
  
 El código siguiente mostrará todos los archivos del directorio actual, imprime el nombre de cada archivo:  
  
 [!code-cpp[NVC_MFCFiles#31](../../mfc/codesnippet/CPP/cfilefind-class_1.cpp)]  
  
 para mantener el ejemplo simple, este código utiliza la clase estándar de `cout` de la biblioteca de C\+\+.  La línea de `cout` se podría reemplazar con una llamada a `CListBox::AddString`, por ejemplo, en un programa con una interfaz gráfica de usuario.  
  
 Para obtener más información sobre cómo utilizar el `CFileFind` y las clases WinInet, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFileFind`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind Class](../../mfc/reference/cftpfilefind-class.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)