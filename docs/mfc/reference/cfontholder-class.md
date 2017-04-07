---
title: Clase CFontHolder | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
dev_langs:
- C++
helpviewer_keywords:
- custom fonts
- CFontHolder class
- fonts, ActiveX controls
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
caps.latest.revision: 19
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
ms.openlocfilehash: fdfa16756ff218159087969f2a4967ed5e76a445
ms.lasthandoff: 02/24/2017

---
# <a name="cfontholder-class"></a>Clase CFontHolder
Implementa la propiedad Font estándar y encapsula la funcionalidad de un objeto de fuente de Windows y de la interfaz de `IFont` .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFontHolder  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFontHolder::CFontHolder](#cfontholder)|Construye un objeto `CFontHolder`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFontHolder::GetDisplayString](#getdisplaystring)|Recupera la cadena que se muestra en el Explorador de propiedades de un contenedor.|  
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Devuelve la fuente `IDispatch` interfaz.|  
|[CFontHolder::GetFontHandle](#getfonthandle)|Devuelve un identificador a una fuente de Windows.|  
|[CFontHolder::InitializeFont](#initializefont)|Inicializa un `CFontHolder` objeto.|  
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Recupera información de la fuente relacionada.|  
|[CFontHolder::ReleaseFont](#releasefont)|Desconecta el `CFontHolder` objeto desde el `IFont` y `IFontNotification` interfaces.|  
|[CFontHolder::Select](#select)|Selecciona un recurso de fuente en un contexto de dispositivo.|  
|[CFontHolder::SetFont](#setfont)|Se conecta la `CFontHolder` objeto un `IFont` interfaz.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFontHolder::m_pFont](#m_pfont)|Un puntero a la `CFontHolder` del objeto `IFont` interfaz.|  
  
## <a name="remarks"></a>Comentarios  
 `CFontHolder`no tiene una clase base.  
  
 Utilice esta clase para implementar propiedades de fuente personalizados para el control. Para obtener información sobre la creación de estas propiedades, vea el artículo [controles ActiveX: utilizar fuentes](../../mfc/mfc-activex-controls-using-fonts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CFontHolder`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
##  <a name="cfontholder"></a>CFontHolder::CFontHolder  
 Construye un objeto `CFontHolder`.  
  
```  
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```  
  
### <a name="parameters"></a>Parámetros  
 *pNotify*  
 Puntero a la fuente `IPropertyNotifySink` interfaz.  
  
### <a name="remarks"></a>Comentarios  
 Se debe llamar a `InitializeFont` para inicializar el objeto resultante antes de usarlo.  
  
##  <a name="getdisplaystring"></a>CFontHolder::GetDisplayString  
 Recupera una cadena que puede mostrarse en el Explorador de propiedades de un contenedor.  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `strValue`  
 Hacer referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) que va a contener la cadena de presentación.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la cadena se recupera correctamente; en caso contrario, 0.  
  
##  <a name="getfontdispatch"></a>CFontHolder::GetFontDispatch  
 Llame a esta función para recuperar un puntero a la interfaz de envío de la fuente.  
  
```  
LPFONTDISP GetFontDispatch();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CFontHolder` del objeto **IFontDisp** interfaz. Tenga en cuenta que la función que llama a `GetFontDispatch` debe llamar a `IUnknown::Release` en este puntero de interfaz cuando termine de usarlo.  
  
### <a name="remarks"></a>Comentarios  
 Llame a `InitializeFont` antes de llamar a `GetFontDispatch`.  
  
##  <a name="getfonthandle"></a>CFontHolder::GetFontHandle  
 Llame a esta función para obtener un identificador a una fuente de Windows.  
  
```  
HFONT GetFontHandle();

 
HFONT GetFontHandle(
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>Parámetros  
 `cyLogical`  
 Alto, en unidades lógicas, del rectángulo en el que se dibujará el control.  
  
 `cyHimetric`  
 Alto, en `MM_HIMETRIC` unidades del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el objeto Font; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 La proporción de `cyLogical` y `cyHimetric` se usa para calcular el tamaño de visualización adecuada, en unidades lógicas, para el tamaño de fuente punto se expresa en `MM_HIMETRIC` unidades:  
  
 Mostrar tamaño = ( `cyLogical`  /  `cyHimetric`) X tamaño de fuente  
  
 La versión sin parámetros devuelve un identificador a una fuente de tamaño correcto para la pantalla.  
  
##  <a name="initializefont"></a>CFontHolder::InitializeFont  
 Inicializa un `CFontHolder` objeto.  
  
```  
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,  
    LPDISPATCH pFontDispAmbient = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFontDesc`  
 Puntero a una estructura de descripción de la fuente ( [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782)) que especifica las características de la fuente.  
  
 `pFontDispAmbient`  
 Puntero a la propiedad de fuente ambiente del contenedor.  
  
### <a name="remarks"></a>Comentarios  
 Si `pFontDispAmbient` no **NULL**, `CFontHolder` objeto está conectado a un clon de la `IFont` interfaz utilizada por la propiedad de fuente ambiente del contenedor.  
  
 Si `pFontDispAmbient` es **NULL**, se crea un nuevo objeto de fuente de la descripción de fuente señalada `pFontDesc` o, si `pFontDesc` es **NULL**, de una descripción predeterminada.  
  
 Llame a esta función después de crear un `CFontHolder` objeto.  
  
##  <a name="m_pfont"></a>CFontHolder::m_pFont  
 Un puntero a la `CFontHolder` del objeto `IFont` interfaz.  
  
```  
LPFONT m_pFont;  
```  
  
##  <a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics  
 Recupera información sobre la fuente física representada por la `CFontHolder` objeto.  
  
```  
void QueryTextMetrics(LPTEXTMETRIC lptm);
```  
  
### <a name="parameters"></a>Parámetros  
 `lptm`  
 Un puntero a un [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) estructura que recibirá la información.  
  
##  <a name="releasefont"></a>CFontHolder::ReleaseFont  
 Esta función se desconecta el `CFontHolder` objeto a partir de su `IFont` interfaz.  
  
```  
void ReleaseFont();
```  
  
##  <a name="select"></a>CFontHolder::Select  
 Llame a esta función para seleccionar la fuente del control en el contexto de dispositivo especificado.  
  
```  
CFont* Select(
    CDC* pDC,  
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Contexto de dispositivo en el que se selecciona la fuente.  
  
 `cyLogical`  
 Alto, en unidades lógicas, del rectángulo en el que se dibujará el control.  
  
 `cyHimetric`  
 Alto, en `MM_HIMETRIC` unidades del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la fuente que se va a reemplazar.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [GetFontHandle](#getfonthandle) para obtener una explicación de la `cyLogical` y `cyHimetric` parámetros.  
  
##  <a name="setfont"></a>CFontHolder::SetFont  
 Libera cualquier fuente existente y se conecta el `CFontHolder` objeto un `IFont` interfaz.  
  
```  
void SetFont(LPFONT pNewFont);
```  
  
### <a name="parameters"></a>Parámetros  
 *pNewFont*  
 Puntero a la nueva `IFont` interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CPropExchange](../../mfc/reference/cpropexchange-class.md)

