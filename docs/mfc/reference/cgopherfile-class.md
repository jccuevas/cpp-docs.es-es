---
title: Clase CGopherFile
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: e157a4509fe30b814a1834690a675906ac82afe7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373690"
---
# <a name="cgopherfile-class"></a>Clase CGopherFile

Proporciona la funcionalidad para buscar y leer archivos en un servidor gopher.

> [!NOTE]
> Las `CGopherConnection`clases `CGopherFileFind` `CGopherLocator` , `CGopherFile`, , y sus miembros han quedado en desuso porque no funcionan en la plataforma Windows XP, pero seguirán funcionando en plataformas anteriores.

## <a name="syntax"></a>Sintaxis

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CGopherFile::CGopherFile](#cgopherfile)|Construye un objeto `CGopherFile`.|

## <a name="remarks"></a>Observaciones

El servicio gopher no permite a los usuarios escribir datos en un archivo gopher porque este servicio funciona principalmente como una interfaz controlada por menús para encontrar información. Las `CGopherFile` `Write`funciones `WriteString`miembro `Flush` , , `CGopherFile`y no se implementan para . Al llamar a `CGopherFile` estas funciones en un objeto, devuelve un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Para obtener más `CGopherFile` información sobre cómo funciona con las otras clases de Internet MFC, vea el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="cgopherfilecgopherfile"></a><a name="cgopherfile"></a>CGopherFile::CGopherFile

Esta función miembro se `CGopherFile` llama para construir un objeto.

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

*hArchivo*<br/>
Identificador de un archivo HINTERNET.

*refLocator*<br/>
Una referencia a un [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.

*pConexión*<br/>
Un puntero a un [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objeto.

*hSesión*<br/>
Un identificador de la sesión de Internet actual.

*pstrLocator*<br/>
Puntero a una cadena utilizada para localizar el servidor gopher. Consulte Sesiones de [Gopher](cgopherlocator-class.md) para obtener más información sobre los localizadores de gopher.

*dwLocLen*<br/>
DWORD que contiene el número de bytes en *pstrLocator*.

*dwContext*<br/>
Puntero al identificador de contexto del archivo que se está abrendo.

### <a name="remarks"></a>Observaciones

Necesita un `CGopherFile` objeto para leer de un archivo durante una sesión de Internet gopher.

Nunca se `CGopherFile` crea un objeto directamente. En su lugar, llame a [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) para abrir un archivo en un servidor gopher.

## <a name="see-also"></a>Consulte también

[Clase CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Clase CGopherLocator](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopherConnection (clase)](../../mfc/reference/cgopherconnection-class.md)
