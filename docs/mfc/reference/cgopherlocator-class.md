---
title: Clase CGopherLocator
ms.date: 11/04/2016
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
ms.openlocfilehash: d23ef3dad68c62e74ec64454953ca372b8c31114
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373676"
---
# <a name="cgopherlocator-class"></a>Clase CGopherLocator

Obtiene un "localizador" gopher de un servidor gopher, determina el tipo del localizador y hace que el localizador esté disponible para [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).

> [!NOTE]
> Las `CGopherConnection`clases `CGopherFileFind` `CGopherLocator` , `CGopherFile`, , y sus miembros han quedado en desuso porque no funcionan en la plataforma Windows XP, pero seguirán funcionando en plataformas anteriores.

## <a name="syntax"></a>Sintaxis

```
class CGopherLocator : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Construye un objeto `CGopherLocator`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analiza un localizador gopher y determina sus atributos.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGopherLocator::operador LPCTSTR](#operator_lpctstr)|Accede directamente a `CGopherLocator` los caracteres almacenados en un objeto como una cadena de estilo C.|

## <a name="remarks"></a>Observaciones

Una aplicación debe obtener el localizador de un servidor gopher para poder recuperar información de ese servidor. Una vez que tiene el localizador, debe tratar el localizador como un token opaco.

Cada localizador gopher tiene atributos que determinan el tipo de archivo o servidor encontrado. Consulte [GetLocatorType](#getlocatortype) para obtener una lista de tipos de localizadores gopher.

Normalmente, una aplicación utiliza el localizador para las llamadas a [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) para recuperar una información específica.

Para obtener más `CGopherLocator` información sobre cómo funciona con las otras clases de Internet MFC, vea el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="cgopherlocatorcgopherlocator"></a><a name="cgopherlocator"></a>CGopherLocator::CGopherLocator

Esta función miembro se `CGopherLocator` llama para crear un objeto.

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>Parámetros

*ref*<br/>
Una referencia a `CGopherLocator` un objeto constante.

### <a name="remarks"></a>Observaciones

Nunca se `CGopherLocator` crea un objeto directamente. En su lugar, llame a [CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) para crear y devolver un puntero al `CGopherLocator` objeto.

## <a name="cgopherlocatorgetlocatortype"></a><a name="getlocatortype"></a>CGopherLocator::GetLocatorType

Llame a esta función miembro para obtener el tipo de localizador.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>Parámetros

*dwRef*<br/>
Una referencia a un DWORD que recibirá el tipo de localizador. Consulte **Comentarios** para obtener una tabla de tipos de localizador.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

Los tipos posibles son los siguientes:

|Value|Significado|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|Un archivo de texto ASCII.|
|GOPHER_TYPE_DIRECTORY|Un directorio de elementos Gopher adicionales.|
|GOPHER_TYPE_CSO|Un servidor de la guía telefónica CSO.|
|GOPHER_TYPE_ERROR|Indica una condición de error.|
|GOPHER_TYPE_MAC_BINHEX|Un archivo Macintosh en formato BINHEX.|
|GOPHER_TYPE_DOS_ARCHIVE|Un archivo de archivo DOS.|
|GOPHER_TYPE_UNIX_UUENCODED|Un archivo UUENCODED.|
|GOPHER_TYPE_INDEX_SERVER|Un servidor de índice.|
|GOPHER_TYPE_TELNET|Un servidor Telnet.|
|GOPHER_TYPE_BINARY|Un archivo binario.|
|GOPHER_TYPE_REDUNDANT|Un servidor duplicado. La información contenida en el la que se encuentra es un duplicado del servidor principal. El servidor principal es la última entrada de directorio que no tenía un tipo de GOPHER_TYPE_REDUNDANT.|
|GOPHER_TYPE_TN3270|Un servidor TN3270.|
|GOPHER_TYPE_GIF|Un archivo de gráficos GIF.|
|GOPHER_TYPE_IMAGE|Un archivo de imagen.|
|GOPHER_TYPE_BITMAP|Un archivo de mapa de bits.|
|GOPHER_TYPE_MOVIE|Un archivo de película.|
|GOPHER_TYPE_SOUND|Un archivo de sonido.|
|GOPHER_TYPE_HTML|Documento HTML.|
|GOPHER_TYPE_PDF|Un archivo PDF.|
|GOPHER_TYPE_CALENDAR|Un archivo de calendario.|
|GOPHER_TYPE_INLINE|Un archivo en línea.|
|GOPHER_TYPE_UNKNOWN|El tipo de elemento es desconocido.|
|GOPHER_TYPE_ASK|Un artículo Ask+.|
|GOPHER_TYPE_GOPHER_PLUS|Un elemento Gopher+.|

## <a name="cgopherlocatoroperator-lpctstr"></a><a name="operator_lpctstr"></a>CGopherLocator::operador LPCTSTR

Este útil operador de conversión proporciona un método eficaz para `CGopherLocator` tener acceso a la cadena C terminada en null contenida en un objeto.

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>Valor devuelto

Puntero de carácter a los datos de la cadena.

### <a name="remarks"></a>Observaciones

No se copia ningún carácter; solo se devuelve un puntero.

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)
