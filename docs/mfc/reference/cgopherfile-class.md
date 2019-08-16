---
title: CGopherFile (clase)
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: 9bb242cb53593862cb51e0c193eb739625127adc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380291"
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

*hFile*<br/>
Identificador de un archivo HINTERNET.

*refLocator*<br/>
Una referencia a un [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.

*pConnection*<br/>
Un puntero a un [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objeto.

*hSession*<br/>
Identificador de la sesión actual de Internet.

*pstrLocator*<br/>
Un puntero a una cadena utilizada para buscar el servidor gopher. Consulte [Gopher sesiones](cgopherlocator-class.md) para obtener más información sobre los localizadores gopher.

*dwLocLen*<br/>
Un valor DWORD que contiene el número de bytes en *pstrLocator*.

*dwContext*<br/>
Un puntero al identificador de contexto del archivo que se está abriendo.

### <a name="remarks"></a>Comentarios

Necesita un `CGopherFile` objeto que se va a leer de un archivo durante una sesión de Internet de gopher.

No crear nunca un `CGopherFile` objeto directamente. En su lugar, llame a [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) para abrir un archivo en un servidor gopher.

## <a name="see-also"></a>Vea también

[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherLocator (clase)](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopherConnection (clase)](../../mfc/reference/cgopherconnection-class.md)
