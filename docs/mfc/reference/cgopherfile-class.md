---
title: CGopherFile (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
dev_langs:
- C++
helpviewer_keywords:
- gopher protocol files
- Internet, gopher
- CGopherFile class
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 40c1e385d0f58095c2aa79cc23168fc00f48ed9b
ms.lasthandoff: 02/24/2017

---
# <a name="cgopherfile-class"></a>CGopherFile (clase)
Proporciona la funcionalidad para buscar y leer archivos en un servidor gopher.  
  
> [!NOTE]
>  Las clases de `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros han quedado en desuso porque no funcionan en la plataforma Windows XP, pero seguirá funcionando en plataformas anteriores.  
  
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
 El servicio gopher no permite a los usuarios escribir datos en un archivo gopher porque este servicio funciona principalmente como una interfaz de menús para buscar información. El `CGopherFile` funciones miembro **escribir**, `WriteString`, y `Flush` no se implementan para `CGopherFile`. Llamar a estas funciones en una `CGopherFile` objeto devuelve un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Para obtener más información acerca de cómo `CGopherFile` funciona con otras clases de Internet de MFC, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="cgopherfile"></a>CGopherFile::CGopherFile  
 Llama a esta función miembro para construir un `CGopherFile` objeto.  
  
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
 Un puntero a una cadena utilizada para buscar el servidor gopher. Consulte [sesiones Gopher](https://msdn.microsoft.com/library/24wz8xze.aspx) para obtener más información acerca de los localizadores de gopher.  
  
 *dwLocLen*  
 Un valor de DWORD que contiene el número de bytes en `pstrLocator`.  
  
 `dwContext`  
 Puntero al identificador de contexto del archivo está abierto.  
  
### <a name="remarks"></a>Comentarios  
 Necesita una `CGopherFile` objeto que se va a leer desde un archivo durante una sesión de Internet de gopher.  
  
 No cree nunca un `CGopherFile` objeto directamente. En su lugar, llame a [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) para abrir un archivo en un servidor gopher.  
  
## <a name="see-also"></a>Vea también  
 [CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)   
 [Clase de objeto CGopherLocator](../../mfc/reference/cgopherlocator-class.md)   
 [Clase CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)   
 [Clase de objeto CGopherConnection](../../mfc/reference/cgopherconnection-class.md)

