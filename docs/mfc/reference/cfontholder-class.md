---
title: Clase CFontHolder | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5cb28b738822b3e35aa840c731eb11bc2c2b83d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367521"
---
# <a name="cfontholder-class"></a>Clase CFontHolder
Implementa la propiedad Font estándar y encapsula la funcionalidad de un objeto de fuente de Windows y de la interfaz de `IFont` .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFontHolder  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFontHolder::CFontHolder](#cfontholder)|Construye un objeto `CFontHolder`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFontHolder::GetDisplayString](#getdisplaystring)|Recupera la cadena que se muestra en el Explorador de propiedades de un contenedor.|  
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Devuelve la fuente `IDispatch` interfaz.|  
|[CFontHolder::GetFontHandle](#getfonthandle)|Devuelve un identificador a una fuente de Windows.|  
|[CFontHolder::InitializeFont](#initializefont)|Inicializa un `CFontHolder` objeto.|  
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Recupera información de la fuente relacionada.|  
|[CFontHolder::ReleaseFont](#releasefont)|Desconecta el `CFontHolder` objeto desde el `IFont` y `IFontNotification` interfaces.|  
|[CFontHolder::Select](#select)|Selecciona un recurso de fuente en un contexto de dispositivo.|  
|[CFontHolder::SetFont](#setfont)|Se conecta la `CFontHolder` el objeto a un `IFont` interfaz.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFontHolder::m_pFont](#m_pfont)|Un puntero a la `CFontHolder` del objeto `IFont` interfaz.|  
  
## <a name="remarks"></a>Comentarios  
 `CFontHolder` no tiene una clase base.  
  
 Utilice esta clase para implementar propiedades de fuente personalizada para el control. Para obtener información sobre la creación de estas propiedades, vea el artículo [controles ActiveX: usar fuentes](../../mfc/mfc-activex-controls-using-fonts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CFontHolder`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
##  <a name="cfontholder"></a>  CFontHolder::CFontHolder  
 Construye un objeto `CFontHolder`.  
  
```  
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```  
  
### <a name="parameters"></a>Parámetros  
 *pNotify*  
 Puntero a la fuente `IPropertyNotifySink` interfaz.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a `InitializeFont` para inicializar el objeto resultante antes de usarlo.  
  
##  <a name="getdisplaystring"></a>  CFontHolder::GetDisplayString  
 Recupera una cadena que se pueden mostrar en Explorador de propiedades de un contenedor.  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `strValue`  
 Referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) que va a contener la cadena de presentación.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la cadena se ha recuperado correctamente; en caso contrario es 0.  
  
##  <a name="getfontdispatch"></a>  CFontHolder::GetFontDispatch  
 Llame a esta función para recuperar un puntero a la interfaz de envío de la fuente.  
  
```  
LPFONTDISP GetFontDispatch();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CFontHolder` del objeto **IFontDisp** interfaz. Tenga en cuenta que la función que llama `GetFontDispatch` debe llamar a `IUnknown::Release` en este puntero de interfaz cuando termine de usarlo.  
  
### <a name="remarks"></a>Comentarios  
 Llame a `InitializeFont` antes de llamar a `GetFontDispatch`.  
  
##  <a name="getfonthandle"></a>  CFontHolder::GetFontHandle  
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
 Un identificador para el objeto Font; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 La proporción de `cyLogical` y `cyHimetric` se usa para calcular el tamaño de visualización adecuada, en unidades lógicas, para el tamaño de fuente punto se expresa en `MM_HIMETRIC` unidades:  
  
 Mostrar tamaño = ( `cyLogical`  /  `cyHimetric`) X el tamaño de fuente  
  
 La versión sin parámetros devuelve un identificador a una fuente el tamaño correcto de la pantalla.  
  
##  <a name="initializefont"></a>  CFontHolder::InitializeFont  
 Inicializa un `CFontHolder` objeto.  
  
```  
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,  
    LPDISPATCH pFontDispAmbient = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFontDesc`  
 Puntero a una estructura de descripción de fuente ( [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782)) que especifica las características de la fuente.  
  
 `pFontDispAmbient`  
 Puntero a la propiedad de fuente ambiente del contenedor.  
  
### <a name="remarks"></a>Comentarios  
 Si `pFontDispAmbient` no es **NULL**, `CFontHolder` objeto está conectado a un clon de la `IFont` interfaz utilizada por la propiedad de fuente ambiente del contenedor.  
  
 Si `pFontDispAmbient` es **NULL**, se crea un nuevo objeto de fuente de la descripción de la fuente que señala `pFontDesc` o, si `pFontDesc` es **NULL**, de una descripción predeterminada.  
  
 Llame a esta función después de crear un `CFontHolder` objeto.  
  
##  <a name="m_pfont"></a>  CFontHolder::m_pFont  
 Un puntero a la `CFontHolder` del objeto `IFont` interfaz.  
  
```  
LPFONT m_pFont;  
```  
  
##  <a name="querytextmetrics"></a>  CFontHolder::QueryTextMetrics  
 Recupera información sobre la fuente física representada por la `CFontHolder` objeto.  
  
```  
void QueryTextMetrics(LPTEXTMETRIC lptm);
```  
  
### <a name="parameters"></a>Parámetros  
 `lptm`  
 Un puntero a un [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) estructura que va a recibir la información.  
  
##  <a name="releasefont"></a>  CFontHolder::ReleaseFont  
 Esta función se desconecta el `CFontHolder` objeto desde su `IFont` interfaz.  
  
```  
void ReleaseFont();
```  
  
##  <a name="select"></a>  CFontHolder::Select  
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
 Un puntero a la fuente que se va a reemplazar.  
  
### <a name="remarks"></a>Comentarios  
 Vea [GetFontHandle](#getfonthandle) para obtener una descripción de la `cyLogical` y `cyHimetric` parámetros.  
  
##  <a name="setfont"></a>  CFontHolder::SetFont  
 Libera cualquier fuente existente y se conecta el `CFontHolder` el objeto a un `IFont` interfaz.  
  
```  
void SetFont(LPFONT pNewFont);
```  
  
### <a name="parameters"></a>Parámetros  
 *pNewFont*  
 Puntero a la nueva `IFont` interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPropExchange (clase)](../../mfc/reference/cpropexchange-class.md)
