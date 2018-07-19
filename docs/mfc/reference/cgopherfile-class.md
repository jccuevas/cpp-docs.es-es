---
title: CGopherFile (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6c4f87ffb1538e581320e9d6f36e8d4fbc6fc12
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335687"
---
# <a name="cgopherfile-class"></a>CGopherFile (clase)
Proporciona la funcionalidad para buscar y leer archivos en un servidor gopher.  
  
> [!NOTE]
>  Las clases `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros se han quedado en desuso porque no funcionan en la plataforma Windows XP, pero seguirán funcionando en las plataformas anteriores.  
  
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
 El servicio gopher no permite a los usuarios escribir datos en un archivo gopher porque este servicio funciona principalmente como una interfaz controlada en el menú para buscar información. El `CGopherFile` funciones miembro `Write`, `WriteString`, y `Flush` no se implementan para `CGopherFile`. Llamar a estas funciones en un `CGopherFile` objeto devuelve un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Para obtener más información sobre cómo `CGopherFile` funciona con las clases de Internet de MFC, vea el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="cgopherfile"></a>  CGopherFile::CGopherFile  
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
 *hFile*  
 Identificador de un archivo HINTERNET.  
  
 *refLocator*  
 Una referencia a un [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.  
  
 *pConnection*  
 Un puntero a un [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objeto.  
  
 *hSession*  
 Identificador de la sesión actual de Internet.  
  
 *pstrLocator*  
 Un puntero a una cadena utilizada para buscar el servidor gopher. Consulte [Gopher sesiones](cgopherlocator-class.md) para obtener más información sobre los localizadores gopher.  
  
 *dwLocLen*  
 Un valor DWORD que contiene el número de bytes en *pstrLocator*.  
  
 *dwContext*  
 Un puntero al identificador de contexto del archivo que se está abriendo.  
  
### <a name="remarks"></a>Comentarios  
 Necesita un `CGopherFile` objeto que se va a leer de un archivo durante una sesión de Internet de gopher.  
  
 No crear nunca un `CGopherFile` objeto directamente. En su lugar, llame a [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) para abrir un archivo en un servidor gopher.  
  
## <a name="see-also"></a>Vea también  
 [CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)   
 [CGopherLocator (clase)](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection (clase)](../../mfc/reference/cgopherconnection-class.md)
