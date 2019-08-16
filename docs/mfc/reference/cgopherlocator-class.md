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
ms.openlocfilehash: 9ce95a712af6502bff2a2502582a7fa843bf9653
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506169"
---
# <a name="cgopherlocator-class"></a>Clase CGopherLocator

Obtiene un "localizador" Gopher de un servidor gopher, determina el tipo de localizador y pone el localizador a disposición de [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).

> [!NOTE]
>  Las clases `CGopherConnection` `CGopherFile` ,`CGopherLocator` , y sus miembros están desusadas porque no funcionan en la plataforma Windows XP, pero seguirán funcionando en plataformas anteriores. `CGopherFileFind`

## <a name="syntax"></a>Sintaxis

```
class CGopherLocator : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Construye un objeto `CGopherLocator`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analiza un localizador gopher y determina sus atributos.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CGopherLocator:: Operator LPCTSTR](#operator_lpctstr)|Accede directamente a los caracteres almacenados en `CGopherLocator` un objeto como una cadena de estilo C.|

## <a name="remarks"></a>Comentarios

Una aplicación debe obtener el localizador de un servidor gopher para poder recuperar información de ese servidor. Una vez que tenga el localizador, debe tratar el localizador como un token opaco.

Cada localizador Gopher tiene atributos que determinan el tipo de archivo o servidor encontrado. Consulte [GetLocatorType](#getlocatortype) para obtener una lista de los tipos de localizadores Gopher.

Normalmente, una aplicación usa el localizador para las llamadas a [CGopherFileFind:: findfile](../../mfc/reference/cgopherfilefind-class.md#findfile) para recuperar una parte específica de la información.

Para obtener más información sobre `CGopherLocator` cómo funciona con las otras clases de Internet de MFC, vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

##  <a name="cgopherlocator"></a>  CGopherLocator::CGopherLocator

Se llama a esta función miembro para crear `CGopherLocator` un objeto.

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>Parámetros

*ref*<br/>
Referencia a un objeto constante `CGopherLocator` .

### <a name="remarks"></a>Comentarios

Nunca se crea un `CGopherLocator` objeto directamente. En su lugar, llame a [CGopherConnection:: CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) para crear y devolver un puntero `CGopherLocator` al objeto.

##  <a name="getlocatortype"></a>  CGopherLocator::GetLocatorType

Llame a esta función miembro para obtener el tipo de localizador.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>Parámetros

*dwRef*<br/>
Referencia a un valor DWORD que recibirá el tipo de localizador. Vea la **sección Comentarios** para obtener una tabla de tipos de localizador.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Los tipos posibles son los siguientes:

|Valor|Significado|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|Un archivo de texto ASCII.|
|GOPHER_TYPE_DIRECTORY|Directorio de elementos Gopher adicionales.|
|GOPHER_TYPE_CSO|Un servidor de libreta de teléfonos CSO.|
|GOPHER_TYPE_ERROR|Indica una condición de error.|
|GOPHER_TYPE_MAC_BINHEX|Un archivo Macintosh en formato BINHEX.|
|GOPHER_TYPE_DOS_ARCHIVE|Un archivo de almacenamiento de DOS.|
|GOPHER_TYPE_UNIX_UUENCODED|Archivo uuencode.|
|GOPHER_TYPE_INDEX_SERVER|Un servidor de indexación.|
|GOPHER_TYPE_TELNET|A Telnet Server.|
|GOPHER_TYPE_BINARY|Un archivo binario.|
|GOPHER_TYPE_REDUNDANT|Un servidor duplicado. La información contenida en es un duplicado del servidor principal. El servidor principal es la última entrada de directorio que no tenía un tipo GOPHER_TYPE_REDUNDANT.|
|GOPHER_TYPE_TN3270|Un servidor TN3270.|
|GOPHER_TYPE_GIF|Un archivo de gráficos GIF.|
|GOPHER_TYPE_IMAGE|Un archivo de imagen.|
|GOPHER_TYPE_BITMAP|Un archivo de mapa de bits.|
|GOPHER_TYPE_MOVIE|Un archivo de película.|
|GOPHER_TYPE_SOUND|Un archivo de sonido.|
|GOPHER_TYPE_HTML|Documento HTML.|
|GOPHER_TYPE_PDF|Un archivo PDF.|
|GOPHER_TYPE_CALENDAR|Un archivo de calendario.|
|GOPHER_TYPE_INLINE|Archivo insertado.|
|GOPHER_TYPE_UNKNOWN|No se conoce el tipo de elemento.|
|GOPHER_TYPE_ASK|Un elemento Ask +.|
|GOPHER_TYPE_GOPHER_PLUS|Un elemento Gopher +.|

##  <a name="operator_lpctstr"></a>  CGopherLocator::operator LPCTSTR

Este operador de conversión útil proporciona un método eficaz para tener acceso a la cadena de C terminada `CGopherLocator` en NULL incluida en un objeto.

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>Valor devuelto

Puntero de carácter a los datos de la cadena.

### <a name="remarks"></a>Comentarios

No se copia ningún carácter; solo se devuelve un puntero.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)
