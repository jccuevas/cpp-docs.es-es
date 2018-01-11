---
title: Clase CGdiObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2970dddd4711c431b3809127e7eeb6f7cd3f9eb1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cgdiobject-class"></a>Clase CGdiObject
Proporciona una clase base para diferentes clases de objetos de la interfaz de dispositivo gráfico (GDI) de Windows, tales como mapas de bits, regiones, pinceles, lápices, tablas y fuentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CGdiObject : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGdiObject::CGdiObject](#cgdiobject)|Construye un objeto `CGdiObject`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGdiObject::Attach](#attach)|Asocia un objeto GDI de Windows para un `CGdiObject` objeto.|  
|[CGdiObject::CreateStockObject](#createstockobject)|Recupera un identificador a uno de los lápices de acciones predefinidas de Windows, pinceles o las fuentes.|  
|[CGdiObject::DeleteObject](#deleteobject)|Elimina el objeto GDI de Windows asociado a la `CGdiObject` objeto de memoria liberando todo el almacenamiento de sistema asociado al objeto.|  
|[CGdiObject::DeleteTempMap](#deletetempmap)|Elimina cualquier temporal `CGdiObject` objetos creados por `FromHandle`.|  
|[CGdiObject::Detach](#detach)|Desasocia un objeto GDI de Windows desde un `CGdiObject` de objetos y devuelve un identificador para el objeto GDI de Windows.|  
|[CGdiObject::FromHandle](#fromhandle)|Devuelve un puntero a un `CGdiObject` objeto especifica un identificador a un objeto GDI de Windows.|  
|[CGdiObject::GetObject](#getobject)|Rellena un búfer con datos que describen el objeto GDI de Windows asociado a la `CGdiObject` objeto.|  
|[CGdiObject::GetObjectType](#getobjecttype)|Recupera el tipo del objeto GDI.|  
|[CGdiObject::GetSafeHandle](#getsafehandle)|Devuelve `m_hObject` a menos que `this` es `NULL`, en cuyo caso `NULL` se devuelve.|  
|[CGdiObject](#unrealizeobject)|Restablece el origen de un pincel o restablece una paleta lógica.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGdiObject::operator! =](#operator_neq)|Determina si dos objetos GDI lógicamente no son iguales.|  
|[CGdiObject::operator ==](#operator_eq_eq)|Determina si dos objetos GDI son lógicamente iguales.|  
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|Recupera un `HANDLE` para el objeto adjunto de GDI de Windows.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGdiObject::m_hObject](#m_hobject)|A `HANDLE` que contiene el `HBITMAP`, `HPALETTE`, `HRGN`, `HBRUSH`, `HPEN`, o `HFONT` asociado a este objeto.|  
  
## <a name="remarks"></a>Comentarios  
 No cree nunca un `CGdiObject` directamente. En su lugar, se crea un objeto de una de sus clases derivadas, como `CPen` o `CBrush`.  
  
 Para obtener más información sobre `CGdiObject`, consulte [objetos gráficos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="attach"></a>CGdiObject::Attach  
 Asocia un objeto GDI de Windows para un `CGdiObject` objeto.  
  
```  
BOOL Attach(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `hObject`  
 A `HANDLE` a un objeto GDI de Windows (por ejemplo, `HPEN` o `HBRUSH`).  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si son correcta; datos adjuntos en caso contrario es 0.  
  
##  <a name="cgdiobject"></a>CGdiObject::CGdiObject  
 Construye un objeto `CGdiObject`.  
  
```  
CGdiObject();
```  
  
### <a name="remarks"></a>Comentarios  
 No cree nunca un `CGdiObject` directamente. En su lugar, se crea un objeto de una de sus clases derivadas, como `CPen` o **Cbrush**.  
  
##  <a name="createstockobject"></a>CGdiObject::CreateStockObject  
 Recupera un identificador a uno de los lápices de GDI de Windows estándar predefinidos, pinceles o fuentes y adjunta el objeto GDI para la `CGdiObject` objeto.  
  
```  
BOOL CreateStockObject(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Constante que especifica el tipo de objeto estándar deseado. Vea el parámetro *fnObject* para [GetStockObject](http://msdn.microsoft.com/library/windows/desktop/dd144925) en el SDK de Windows para obtener una descripción de los valores adecuados.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llamada a esta función con uno de la clase derivada, las clases que corresponde al tipo de objeto GDI de Windows, como `CPen` para un lápiz estándar.  
  
##  <a name="deleteobject"></a>CGdiObject::DeleteObject  
 Elimina el objeto adjunto de GDI de Windows de la memoria liberando todo el almacenamiento de sistema asociado al objeto GDI de Windows.  
  
```  
BOOL DeleteObject();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se eliminó correctamente el objeto GDI; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 El almacenamiento asociado a la `CGdiObject` objeto no se ve afectado por esta llamada. Una aplicación no debe llamar a `DeleteObject` en un `CGdiObject` objeto actualmente seleccionado en un contexto de dispositivo.  
  
 Cuando se elimina un pincel de modelo, no se elimina el mapa de bits asociado con el pincel. El mapa de bits debe eliminarse por separado.  
  
##  <a name="deletetempmap"></a>CGdiObject::DeleteTempMap  
 Llama de forma automática la `CWinApp` controlador de tiempo de inactividad, `DeleteTempMap` elimina cualquier temporal `CGdiObject` objetos creados por `FromHandle`.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>Comentarios  
 `DeleteTempMap`Desasocia el objeto de GDI de Windows asociado a un archivo temporal `CGdiObject` objeto antes de eliminar el `CGdiObject` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]  
  
##  <a name="detach"></a>CGdiObject::Detach  
 Desasocia un objeto GDI de Windows desde un `CGdiObject` de objetos y devuelve un identificador para el objeto GDI de Windows.  
  
```  
HGDIOBJ Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 A `HANDLE` para Windows GDI objeto desasociado; en caso contrario **NULL** si no está conectado a ningún objeto GDI.  
  
##  <a name="fromhandle"></a>CGdiObject::FromHandle  
 Devuelve un puntero a un `CGdiObject` objeto especifica un identificador a un objeto GDI de Windows.  
  
```  
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `hObject`  
 Un `HANDLE` a un objeto GDI de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CGdiObject` que puede ser temporal o permanente.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CGdiObject` objeto ya no está asociado al objeto GDI de Windows, un archivo temporal `CGdiObject` se crea y asocia el objeto.  
  
 Este temporal `CGdiObject` objeto solo es válido hasta la próxima vez que la aplicación no tiene tiempo de inactividad en su bucle de eventos, en qué momento se eliminan todos los objetos temporales de gráficos. Otra manera de decir esto es que el objeto temporal sólo es válido durante el procesamiento de mensajes de una ventana.  
  
##  <a name="getobject"></a>CGdiObject::GetObject  
 Llena un búfer de datos que define un objeto especificado.  
  
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
 Recupera el número de bytes; en caso contrario, 0 si un error se produce.  
  
### <a name="remarks"></a>Comentarios  
 La función recupera una estructura de datos cuyo tipo depende del tipo de objeto gráfico, como se muestra en la lista siguiente:  
  
|Object|Tipo de búfer|  
|------------|-----------------|  
|`CPen`|[LOGPEN](../../mfc/reference/logpen-structure.md)|  
|`CBrush`|[LOGBRUSH](../../mfc/reference/logbrush-structure.md)|  
|`CFont`|[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)|  
|`CBitmap`|[MAPA DE BITS](../../mfc/reference/bitmap-structure.md)|  
|`CPalette`|**WORD**|  
|`CRgn`|No compatibles|  
  
 Si el objeto es un `CBitmap` objeto, `GetObject` devuelve el ancho, alto y la información de formato de color del mapa de bits. Los bits reales se pueden recuperar mediante el uso de [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).  
  
 Si el objeto es un `CPalette` objeto, `GetObject` recupera un **WORD** que especifica el número de entradas de la paleta. La función no recupera el [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) estructura que define la paleta. Una aplicación puede obtener información sobre las entradas de la paleta mediante una llamada a [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).  
  
##  <a name="getobjecttype"></a>CGdiObject::GetObjectType  
 Recupera el tipo del objeto GDI.  
  
```  
UINT GetObjectType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tipo del objeto, si se realiza correctamente; en caso contrario es 0. El valor puede ser uno de los siguientes:  
  
- **OBJ_BITMAP** mapa de bits  
  
- **OBJ_BRUSH** pincel  
  
- **OBJ_FONT** fuente  
  
- **OBJ_PAL** paleta  
  
- **OBJ_PEN** lápiz  
  
- **OBJ_EXTPEN** Extended pluma  
  
- **OBJ_REGION** región  
  
- **OBJ_DC** contexto de dispositivo  
  
- **OBJ_MEMDC** contexto de dispositivo de memoria  
  
- **OBJ_METAFILE** metarchivo  
  
- **OBJ_METADC** contexto de dispositivo de metarchivo  
  
- **OBJ_ENHMETAFILE** metarchivo mejorado  
  
- **OBJ_ENHMETADC** contexto de dispositivo de metarchivo mejorado  
  
##  <a name="getsafehandle"></a>CGdiObject::GetSafeHandle  
 Devuelve `m_hObject` a menos que **esto** es **NULL**, en cuyo caso **NULL** se devuelve.  
  
```  
HGDIOBJ GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A `HANDLE` para el objeto GDI de Windows asociado; en caso contrario, **NULL** si no está conectado a ningún objeto.  
  
### <a name="remarks"></a>Comentarios  
 Esto forma parte del paradigma de interfaz de controlador general y es útil cuando **NULL** es un valor válido o especial para un identificador.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).  
  
##  <a name="m_hobject"></a>CGdiObject::m_hObject  
 A `HANDLE` que contiene el `HBITMAP`, **HRGN**, `HBRUSH`, `HPEN`, `HPALETTE`, o **HFONT** asociado a este objeto.  
  
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
 Recupera un `HANDLE` para el objeto GDI de Windows asociado; en caso contrario, **NULL** si no está conectado a ningún objeto.  
  
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
 Mientras `UnrealizeObject` es una función miembro de la `CGdiObject` (clase), se debe invocar solo en `CBrush` o `CPalette` objetos.  
  
 Para `CBrush` objetos, `UnrealizeObject` indica al sistema para restablecer el origen del pincel determinado la próxima vez que se selecciona en un contexto de dispositivo. Si el objeto es un `CPalette` objeto, `UnrealizeObject` indica al sistema que tenga en cuenta la paleta como si hubiera no previamente ha realizado. La próxima vez que la aplicación llama a la [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) función de la paleta especificada, el sistema reasigna completamente la paleta lógica a la paleta del sistema.  
  
 El `UnrealizeObject` función no debe usarse con objetos estándar. El `UnrealizeObject` función debe llamarse siempre que se establece un nuevo origen de pincel (por medio de la [CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) función). El `UnrealizeObject` función no debe llamarse para el pincel seleccionado actualmente o la paleta seleccionada actualmente de cualquier contexto de presentación.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CBitmap (clase)](../../mfc/reference/cbitmap-class.md)   
 [CBrush (clase)](../../mfc/reference/cbrush-class.md)   
 [CFont (clase)](../../mfc/reference/cfont-class.md)   
 [CPalette (clase)](../../mfc/reference/cpalette-class.md)   
 [CPen (clase)](../../mfc/reference/cpen-class.md)   
 [CRgn (clase)](../../mfc/reference/crgn-class.md)
