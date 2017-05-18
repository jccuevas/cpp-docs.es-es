---
title: Clase CGdiObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
dev_langs:
- C++
helpviewer_keywords:
- brushes, base class for
- fonts, base class for
- regions, base class for
- pens, base class for
- palettes, base class for
- CGdiObject class
- GDI objects, base class for
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
caps.latest.revision: 21
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7fb0cd49c6a20263a5cae305b7f08f2733033ff2
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cgdiobject-class"></a>Clase CGdiObject
Proporciona una clase base para diferentes clases de objetos de la interfaz de dispositivo gráfico (GDI) de Windows, tales como mapas de bits, regiones, pinceles, lápices, tablas y fuentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CGdiObject : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CGdiObject::CGdiObject](#cgdiobject)|Construye un objeto `CGdiObject`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CGdiObject::Attach](#attach)|Adjunta un objeto GDI de Windows a un `CGdiObject` objeto.|  
|[CGdiObject::CreateStockObject](#createstockobject)|Recupera un identificador a uno de los lápices de acciones predefinidas de Windows, pinceles o las fuentes.|  
|[CGdiObject::DeleteObject](#deleteobject)|Elimina el objeto de GDI de Windows asociado a la `CGdiObject` objeto de la memoria al liberar todo el almacenamiento de sistema asociado al objeto.|  
|[CGdiObject::DeleteTempMap](#deletetempmap)|Elimina cualquier temporal `CGdiObject` objetos creados por `FromHandle`.|  
|[CGdiObject::Detach](#detach)|Desasocia un objeto GDI de Windows desde un `CGdiObject` de objetos y devuelve un identificador para el objeto de GDI de Windows.|  
|[CGdiObject::FromHandle](#fromhandle)|Devuelve un puntero a un `CGdiObject` objeto asignado un identificador a un objeto de GDI de Windows.|  
|[CGdiObject::GetObject](#getobject)|Llena un búfer con datos que describe el objeto de GDI de Windows asociado a la `CGdiObject` objeto.|  
|[CGdiObject::GetObjectType](#getobjecttype)|Recupera el tipo del objeto GDI.|  
|[CGdiObject::GetSafeHandle](#getsafehandle)|Devuelve `m_hObject` a menos que `this` es `NULL`, en cuyo caso `NULL` se devuelve.|  
|[CGdiObject](#unrealizeobject)|Restablece el origen de un pincel o restablece una paleta lógica.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CGdiObject::operator! =](#operator_neq)|Determina si dos objetos GDI lógicamente no son iguales.|  
|[CGdiObject::operator ==](#operator_eq_eq)|Determina si dos objetos GDI son lógicamente iguales.|  
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|Recupera un `HANDLE` el objeto GDI de Windows.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CGdiObject::m_hObject](#m_hobject)|Un `HANDLE` que contiene el `HBITMAP`, `HPALETTE`, `HRGN`, `HBRUSH`, `HPEN`, o `HFONT` asociado a este objeto.|  
  
## <a name="remarks"></a>Comentarios  
 No cree nunca un `CGdiObject` directamente. En su lugar, se crea un objeto de una de sus clases derivadas, como `CPen` o `CBrush`.  
  
 Para obtener más información sobre `CGdiObject`, consulte [objetos gráficos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="attach"></a>CGdiObject::Attach  
 Adjunta un objeto GDI de Windows a un `CGdiObject` objeto.  
  
```  
BOOL Attach(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `hObject`  
 Un `HANDLE` a un objeto GDI de Windows (por ejemplo, `HPEN` o `HBRUSH`).  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el dato adjunto es correcto; en caso contrario, 0.  
  
##  <a name="cgdiobject"></a>CGdiObject::CGdiObject  
 Construye un objeto `CGdiObject`.  
  
```  
CGdiObject();
```  
  
### <a name="remarks"></a>Comentarios  
 No cree nunca un `CGdiObject` directamente. En su lugar, se crea un objeto de una de sus clases derivadas, como `CPen` o **Cbrush**.  
  
##  <a name="createstockobject"></a>CGdiObject::CreateStockObject  
 Recupera un identificador a uno de los lápices de GDI de Windows estándar predefinidos, pinceles o fuentes y adjunta el objeto GDI a la `CGdiObject` objeto.  
  
```  
BOOL CreateStockObject(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Constante que especifica el tipo de objeto estándar que desee. Vea el parámetro *fnObject* de [GetStockObject](http://msdn.microsoft.com/library/windows/desktop/dd144925) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una descripción de los valores adecuados.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llamada a esta función con uno de los derivados de las clases que corresponde al tipo de objeto GDI de Windows, como `CPen` para un lápiz estándar.  
  
##  <a name="deleteobject"></a>CGdiObject::DeleteObject  
 Elimina el objeto GDI de Windows desde la memoria liberando todo el almacenamiento de sistema asociado con el objeto de GDI de Windows.  
  
```  
BOOL DeleteObject();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se eliminó correctamente el objeto GDI; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El almacenamiento asociado con el `CGdiObject` objeto no se ve afectado por esta llamada. Una aplicación no debe llamar a `DeleteObject` en un `CGdiObject` objeto actualmente seleccionado en un contexto de dispositivo.  
  
 Cuando se elimina un pincel de modelo, no se elimina el mapa de bits asociado con el pincel. El mapa de bits debe eliminarse por separado.  
  
##  <a name="deletetempmap"></a>CGdiObject::DeleteTempMap  
 Llama de forma automática el `CWinApp` controlador de tiempo de inactividad, `DeleteTempMap` elimina cualquier temporal `CGdiObject` objetos creados por `FromHandle`.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>Comentarios  
 `DeleteTempMap`Desasocia el objeto de GDI de Windows asociado a un objeto temporal `CGdiObject` objeto antes de eliminar el `CGdiObject` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#175;](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]  
  
##  <a name="detach"></a>CGdiObject::Detach  
 Desasocia un objeto GDI de Windows desde un `CGdiObject` de objetos y devuelve un identificador para el objeto de GDI de Windows.  
  
```  
HGDIOBJ Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `HANDLE` en el GDI de Windows objeto desasociado; en caso contrario **NULL** si no está conectado a ningún objeto GDI.  
  
##  <a name="fromhandle"></a>CGdiObject::FromHandle  
 Devuelve un puntero a un `CGdiObject` objeto asignado un identificador a un objeto de GDI de Windows.  
  
```  
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `hObject`  
 Un `HANDLE` a un objeto GDI de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CGdiObject` que puede ser temporal o permanente.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CGdiObject` objeto no está asociado al objeto GDI de Windows, un archivo temporal `CGdiObject` objeto creado y conectado.  
  
 Este temporal `CGdiObject` objeto solo es válido hasta la próxima vez que la aplicación tiene el tiempo de inactividad en el bucle de eventos, en qué momento se eliminan todos los objetos de gráficos temporales. Otra forma de decir esto es que el objeto temporal sólo es válido durante el procesamiento de mensajes de una ventana.  
  
##  <a name="getobject"></a>CGdiObject::GetObject  
 Llena un búfer con datos que define un objeto especificado.  
  
```  
int GetObject(
    int nCount,  
    LPVOID lpObject) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nCount`  
 Especifica el número de bytes que se va a copiar en el `lpObject` búfer.  
  
 `lpObject`  
 Señala a un búfer proporcionado por el usuario que va a recibir la información.  
  
### <a name="return-value"></a>Valor devuelto  
 Recupera el número de bytes; de lo contrario, 0 si un error se produce.  
  
### <a name="remarks"></a>Comentarios  
 La función recupera una estructura de datos cuyo tipo depende del tipo de objeto gráfico, como se muestra en la siguiente lista:  
  
|Objeto|Tipo de búfer|  
|------------|-----------------|  
|`CPen`|[LOGPEN](../../mfc/reference/logpen-structure.md)|  
|`CBrush`|[LOGBRUSH](../../mfc/reference/logbrush-structure.md)|  
|`CFont`|[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)|  
|`CBitmap`|[MAPA DE BITS](../../mfc/reference/bitmap-structure.md)|  
|`CPalette`|**WORD**|  
|`CRgn`|No compatibles|  
  
 Si el objeto es un `CBitmap` objeto, `GetObject` devuelve el ancho, alto y la información de formato de color del mapa de bits. Los bits reales se pueden recuperar mediante [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).  
  
 Si el objeto es un `CPalette` objeto, `GetObject` recupera un **WORD** que especifica el número de entradas en la paleta. La función no recupera el [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) estructura que define la paleta. Una aplicación puede obtener información sobre las entradas de paleta llamando a [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).  
  
##  <a name="getobjecttype"></a>CGdiObject::GetObjectType  
 Recupera el tipo del objeto GDI.  
  
```  
UINT GetObjectType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tipo del objeto, si es correcto; en caso contrario, 0. El valor puede ser uno de los siguientes:  
  
- **OBJ_BITMAP** mapa de bits  
  
- **OBJ_BRUSH** pincel  
  
- **OBJ_FONT** fuente  
  
- **OBJ_PAL** paleta  
  
- **OBJ_PEN** lápiz  
  
- **OBJ_EXTPEN** lápiz extendido  
  
- **OBJ_REGION** región  
  
- **OBJ_DC** el contexto de dispositivo  
  
- **OBJ_MEMDC** contexto de dispositivo de memoria  
  
- **OBJ_METAFILE** metarchivo  
  
- **OBJ_METADC** el contexto de dispositivo de metarchivo  
  
- **OBJ_ENHMETAFILE** metarchivo mejorado  
  
- **OBJ_ENHMETADC** contexto de dispositivo de metarchivo mejorado  
  
##  <a name="getsafehandle"></a>CGdiObject::GetSafeHandle  
 Devuelve `m_hObject` a menos que **esto** es **NULL**, en cuyo caso **NULL** se devuelve.  
  
```  
HGDIOBJ GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `HANDLE` el objeto GDI de Windows; de lo contrario, **NULL** si no está conectado a ningún objeto.  
  
### <a name="remarks"></a>Comentarios  
 Esto forma parte del paradigma de interfaz de controlador general y es útil cuando **NULL** es un valor válido o especial para un identificador.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).  
  
##  <a name="m_hobject"></a>CGdiObject::m_hObject  
 Un `HANDLE` que contiene el `HBITMAP`, **HRGN**, `HBRUSH`, `HPEN`, `HPALETTE`, o **HFONT** asociado a este objeto.  
  
```  
HGDIOBJ m_hObject;  
```  
  
##  <a name="operator_neq"></a>CGdiObject::operator! =  
 Determina si dos objetos GDI lógicamente no son iguales.  
  
```  
BOOL operator!=(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `obj`  
 Un puntero a un archivo `CGdiObject`.  
  
### <a name="remarks"></a>Comentarios  
 Determina si un objeto GDI en el lado izquierdo no es igual a un objeto GDI en el lado derecho.  
  
##  <a name="operator_eq_eq"></a>CGdiObject::operator ==  
 Determina si dos objetos GDI son lógicamente iguales.  
  
```  
BOOL operator==(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `obj`  
 Una referencia a un archivo `CGdiObject`.  
  
### <a name="remarks"></a>Comentarios  
 Determina si un objeto GDI en el lado izquierdo es igual a un objeto GDI en el lado derecho.  
  
##  <a name="operator_hgdiobj"></a>CGdiObject::operator HGDIOBJ  
 Recupera un `HANDLE` el objeto GDI de Windows; de lo contrario, **NULL** si no está conectado a ningún objeto.  
  
```  
operator HGDIOBJ() const;  
```  
  
##  <a name="unrealizeobject"></a>CGdiObject  
 Restablece el origen de un pincel o restablece una paleta lógica.  
  
```  
BOOL UnrealizeObject();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Mientras `UnrealizeObject` es una función miembro de la `CGdiObject` (clase), se debe invocar en `CBrush` o `CPalette` objetos.  
  
 Para `CBrush` objetos, `UnrealizeObject` indica al sistema que restablece el origen del pincel dado la próxima vez que está seleccionado en un contexto de dispositivo. Si el objeto es un `CPalette` objeto, `UnrealizeObject` indica al sistema que tenga en cuenta la paleta como si hubiera no previamente ha realizado. La próxima vez que la aplicación llama a la [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) función de la paleta especificada, el sistema vuelve a asignar completamente la paleta lógica a la paleta del sistema.  
  
 El `UnrealizeObject` función no debe usarse con objetos estándar. El `UnrealizeObject` debe llamar la función siempre que se establezca un nuevo origen de pincel (por medio de la [CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) función). El `UnrealizeObject` no se debe llamar la función para el pincel seleccionado actualmente o la paleta seleccionada actualmente de cualquier contexto de presentación.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CBitmap (clase)](../../mfc/reference/cbitmap-class.md)   
 [CBrush (clase)](../../mfc/reference/cbrush-class.md)   
 [CFont (clase)](../../mfc/reference/cfont-class.md)   
 [CPalette (clase)](../../mfc/reference/cpalette-class.md)   
 [CPen (clase)](../../mfc/reference/cpen-class.md)   
 [CRgn (clase)](../../mfc/reference/crgn-class.md)

