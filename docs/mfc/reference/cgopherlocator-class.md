---
title: Clase de objeto CGopherLocator | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
dev_langs:
- C++
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffe833195e665fad37c6638c83170a1913197d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cgopherlocator-class"></a>Clase de objeto CGopherLocator
Obtiene un "localizador gopher" de un servidor gopher, determina el tipo de localizador y pone el localizador a disposición [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).  
  
> [!NOTE]
>  Las clases de `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros se han quedado en desuso porque no funcionan en la plataforma Windows XP, pero continuarán funcionando en plataformas anteriores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CGopherLocator : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Construye un objeto `CGopherLocator`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analiza un localizador gopher y determina sus atributos.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|Obtiene acceso directamente a los caracteres que se almacenan en un `CGopherLocator` objeto como una cadena de estilo C.|  
  
## <a name="remarks"></a>Comentarios  
 Una aplicación debe obtener la ubicación de un servidor gopher antes de poder recuperar la información de ese servidor. Cuando tenga el localizador, debe tratar el localizador como un token opaco.  
  
 Cada localizador gopher tiene atributos que determinan el tipo de archivo o se encontró el servidor. Vea [GetLocatorType](#getlocatortype) para obtener una lista de tipos de localizadores gopher.  
  
 Normalmente, una aplicación usa el localizador para las llamadas a [CGopherFileFind:: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) para recuperar una parte específica de la información.  
  
 Para obtener más información sobre cómo `CGopherLocator` funciona con las demás clases de Internet de MFC, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="cgopherlocator"></a>CGopherLocator::CGopherLocator  
 Esta función miembro se llama para crear un `CGopherLocator` objeto.  
  
```  
CGopherLocator(const CGopherLocator& ref);
```  
  
### <a name="parameters"></a>Parámetros  
 `ref`  
 Una referencia a una constante `CGopherLocator` objeto.  
  
### <a name="remarks"></a>Comentarios  
 No cree nunca un `CGopherLocator` objeto directamente. En su lugar, llame a [CGopherConnection:: CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) para crear y devolver un puntero a la `CGopherLocator` objeto.  
  
##  <a name="getlocatortype"></a>CGopherLocator::GetLocatorType  
 Llame a esta función miembro para obtener el tipo de localizador.  
  
```  
BOOL GetLocatorType(DWORD& dwRef) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *dwRef*  
 Una referencia a un `DWORD` que recibirá el tipo de localizador. Vea **comentarios** para una tabla de tipos de localizador.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 Los tipos posibles son los siguientes:  
  
|Valor|Significado|  
|-----------|-------------|  
|GOPHER_TYPE_TEXT_FILE|Un archivo de texto ASCII.|  
|GOPHER_TYPE_DIRECTORY|Un directorio de elementos adicionales de Gopher.|  
|GOPHER_TYPE_CSO|Un servidor de libreta de teléfonos CSO.|  
|GOPHER_TYPE_ERROR|Indica una condición de error.|  
|GOPHER_TYPE_MAC_BINHEX|Un archivo de Macintosh en formato BINHEX.|  
|GOPHER_TYPE_DOS_ARCHIVE|Un archivo de almacenamiento de DOS.|  
|GOPHER_TYPE_UNIX_UUENCODED|Un archivo con codificación uuencode.|  
|GOPHER_TYPE_INDEX_SERVER|Un servidor de indexación.|  
|GOPHER_TYPE_TELNET|Un servidor Telnet.|  
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
|GOPHER_TYPE_INLINE|Un archivo en línea.|  
|GOPHER_TYPE_UNKNOWN|Se desconoce el tipo de elemento.|  
|GOPHER_TYPE_ASK|Un elemento que pida +.|  
|GOPHER_TYPE_GOPHER_PLUS|Un elemento Gopher +.|  
  
##  <a name="operator_lpctstr"></a>CGopherLocator::operator LPCTSTR  
 Este operador de conversión útil proporciona un método eficaz para tener acceso a la cadena de C terminada en null contenida en un `CGopherLocator` objeto.  
  
```  
operator LPCTSTR () const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero de carácter a los datos de la cadena.  
  
### <a name="remarks"></a>Comentarios  
 No se copian caracteres; se devuelve solo un puntero.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)
