---
title: Clase de objeto CGopherLocator | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherLocator
dev_langs:
- C++
helpviewer_keywords:
- gopher locator
- CGopherLocator class
- Internet, gopher searches
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c5c9b862714d046bc81a49dda27fd5fc062b9ba8
ms.lasthandoff: 02/24/2017

---
# <a name="cgopherlocator-class"></a>Clase de objeto CGopherLocator
Obtiene un "localizador gopher" de un servidor gopher, determina el tipo de localizador y pone el localizador a disposición [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).  
  
> [!NOTE]
>  Las clases de `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros han quedado en desuso porque no funcionan en la plataforma Windows XP, pero seguirá funcionando en plataformas anteriores.  
  
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
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|Obtiene acceso directamente a los caracteres que se almacenan en un `CGopherLocator` objeto como una cadena de estilo C.|  
  
## <a name="remarks"></a>Comentarios  
 Una aplicación debe obtener la ubicación de un servidor gopher antes de poder recuperar la información de ese servidor. Cuando tenga el localizador, debe tratar el localizador como un token opaco.  
  
 Cada localizador gopher tiene atributos que determinan el tipo de archivo o se encuentra el servidor. Consulte [GetLocatorType](#getlocatortype) para obtener una lista de tipos de localizadores gopher.  
  
 Una aplicación normalmente utiliza el localizador de llamadas a [CGopherFileFind:: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) para recuperar una parte específica de la información.  
  
 Para obtener más información acerca de cómo `CGopherLocator` funciona con otras clases de Internet de MFC, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="a-namecgopherlocatora--cgopherlocatorcgopherlocator"></a><a name="cgopherlocator"></a>CGopherLocator::CGopherLocator  
 Esta función miembro se llama para crear una `CGopherLocator` objeto.  
  
```  
CGopherLocator(const CGopherLocator& ref);
```  
  
### <a name="parameters"></a>Parámetros  
 `ref`  
 Una referencia a una constante `CGopherLocator` objeto.  
  
### <a name="remarks"></a>Comentarios  
 No cree nunca un `CGopherLocator` objeto directamente. En su lugar, llame a [CGopherConnection:: CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) para crear y devolver un puntero a la `CGopherLocator` objeto.  
  
##  <a name="a-namegetlocatortypea--cgopherlocatorgetlocatortype"></a><a name="getlocatortype"></a>CGopherLocator::GetLocatorType  
 Llame a esta función miembro para obtener el tipo de localizador.  
  
```  
BOOL GetLocatorType(DWORD& dwRef) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *dwRef*  
 Una referencia a un `DWORD` que recibirá el tipo de localizador. Consulte **comentarios** para una tabla de tipos de localizador.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamar para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 Los tipos posibles son:  
  
|Valor|Significado|  
|-----------|-------------|  
|GOPHER_TYPE_TEXT_FILE|Un archivo de texto ASCII.|  
|GOPHER_TYPE_DIRECTORY|Directorio de elementos adicionales de Gopher.|  
|GOPHER_TYPE_CSO|Un servidor de la libreta de teléfonos CSO.|  
|GOPHER_TYPE_ERROR|Indica una condición de error.|  
|GOPHER_TYPE_MAC_BINHEX|Un archivo de Macintosh en formato BINHEX.|  
|GOPHER_TYPE_DOS_ARCHIVE|Un archivo de denegación de servicio.|  
|GOPHER_TYPE_UNIX_UUENCODED|Un archivo con codificación uuencode.|  
|GOPHER_TYPE_INDEX_SERVER|Un servidor de indexación.|  
|GOPHER_TYPE_TELNET|Un servidor Telnet.|  
|GOPHER_TYPE_BINARY|Un archivo binario.|  
|GOPHER_TYPE_REDUNDANT|Un servidor duplicado. La información contenida en es un duplicado del servidor principal. El servidor principal es la última entrada de directorio que no tiene un tipo GOPHER_TYPE_REDUNDANT.|  
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
|GOPHER_TYPE_ASK|Ask + elemento.|  
|GOPHER_TYPE_GOPHER_PLUS|Un elemento Gopher +.|  
  
##  <a name="a-nameoperatorlpctstra--cgopherlocatoroperator-lpctstr"></a><a name="operator_lpctstr"></a>CGopherLocator::operator LPCTSTR  
 Este operador de conversión útil proporciona un método eficaz para tener acceso a la cadena de C terminada en null, contenida en una `CGopherLocator` objeto.  
  
```  
operator LPCTSTR () const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a los datos de la cadena de carácter.  
  
### <a name="remarks"></a>Comentarios  
 No se copian caracteres; se devuelve sólo un puntero.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)

