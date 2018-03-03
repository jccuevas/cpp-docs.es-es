---
title: CGopherFile (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
dev_langs:
- C++
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce90eb2baf4ce8f6ba0136a9efd503086b686aa6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cgopherfile-class"></a>CGopherFile (clase)
Proporciona la funcionalidad para buscar y leer archivos en un servidor gopher.  
  
> [!NOTE]
>  Las clases de `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros se han quedado en desuso porque no funcionan en la plataforma Windows XP, pero continuarán funcionando en plataformas anteriores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CGopherFile : public CInternetFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherFile::CGopherFile](#cgopherfile)|Construye un objeto `CGopherFile`.|  
  
## <a name="remarks"></a>Comentarios  
 El servicio gopher no permite a los usuarios escribir datos en un archivo gopher porque este servicio funciona principalmente como una interfaz basada en menús para buscar información. El `CGopherFile` funciones miembro **escribir**, `WriteString`, y `Flush` no se implementan para `CGopherFile`. Al llamar a estas funciones en un `CGopherFile` objeto devuelve un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Para obtener más información sobre cómo `CGopherFile` funciona con las demás clases de Internet de MFC, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="cgopherfile"></a>CGopherFile::CGopherFile  
 Se llama a esta función miembro para construir un `CGopherFile` objeto.  
  
```  
CGopherFile(
    HINTERNET hFile,  
    CGopherLocator& refLocator,  
    CGopherConnection* pConnection);

 
CGopherFile(
    HINTERNET hFile,  
    HINTERNET hSession,  
    LPCTSTR pstrLocator,  
    DWORD dwLocLen,  
    DWORD_PTR dwContext);
```  
  
### <a name="parameters"></a>Parámetros  
 `hFile`  
 Un identificador de un `HINTERNET` archivo.  
  
 `refLocator`  
 Una referencia a un [objeto CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.  
  
 `pConnection`  
 Un puntero a un [objeto CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objeto.  
  
 `hSession`  
 Identificador de la sesión actual de Internet.  
  
 `pstrLocator`  
 Un puntero a una cadena utilizada para buscar el servidor gopher. Vea [sesiones Gopher](cgopherlocator-class.md) para obtener más información sobre los localizadores de gopher.  
  
 *dwLocLen*  
 Un valor de DWORD que contiene el número de bytes en `pstrLocator`.  
  
 `dwContext`  
 Un puntero al identificador de contexto del archivo que se va a abrir.  
  
### <a name="remarks"></a>Comentarios  
 Necesita un `CGopherFile` objeto que se va a leer de un archivo durante una sesión de Internet de gopher.  
  
 No cree nunca un `CGopherFile` objeto directamente. En su lugar, llame a [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) para abrir un archivo en un servidor gopher.  
  
## <a name="see-also"></a>Vea también  
 [CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)   
 [Clase de objeto CGopherLocator](../../mfc/reference/cgopherlocator-class.md)   
 [Clase CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection (clase)](../../mfc/reference/cgopherconnection-class.md)
