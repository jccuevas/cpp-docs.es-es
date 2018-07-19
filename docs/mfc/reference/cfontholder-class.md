---
title: CFontHolder (clase) | Microsoft Docs
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
ms.openlocfilehash: 3c110c0addfe14ed8ba9018345eb1f4e61fd5182
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338625"
---
# <a name="cfontholder-class"></a>CFontHolder (clase)
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
|[CFontHolder::SetFont](#setfont)|Se conecta el `CFontHolder` objeto a un `IFont` interfaz.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFontHolder::m_pFont](#m_pfont)|Un puntero a la `CFontHolder` del objeto `IFont` interfaz.|  
  
## <a name="remarks"></a>Comentarios  
 `CFontHolder` no tiene una clase base.  
  
 Utilice esta clase para implementar las propiedades de fuente personalizada para el control. Para obtener información sobre la creación de estas propiedades, vea el artículo [controles ActiveX: usar fuentes](../../mfc/mfc-activex-controls-using-fonts.md).  
  
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
 Recupera una cadena que se puede mostrar en Explorador de propiedades de un contenedor.  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>Parámetros  
 *strValue*  
 Hacer referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) que consiste en conservar la cadena de presentación.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la cadena se recupera correctamente; en caso contrario, es 0.  
  
##  <a name="getfontdispatch"></a>  CFontHolder::GetFontDispatch  
 Llame a esta función para recuperar un puntero a la interfaz de envío de la fuente.  
  
```  
LPFONTDISP GetFontDispatch();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CFontHolder` del objeto `IFontDisp` interfaz. Tenga en cuenta que la función que llama a `GetFontDispatch` debe llamar a `IUnknown::Release` en este puntero de interfaz cuando haya terminado con él.  
  
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
 *cyLogical*  
 Alto, en unidades lógicas, del rectángulo en el que se dibuja el control.  
  
 *cyHimetric*  
 Alto, en unidades MM_HIMETRIC, del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el objeto de fuente; en caso contrario, es NULL.  
  
### <a name="remarks"></a>Comentarios  
 La proporción de *cyLogical* y *cyHimetric* se usa para calcular el tamaño de visualización adecuada, en unidades lógicas, para el tamaño de fuente punto expresado en unidades MM_HIMETRIC:  
  
 Tamaño de presentación = ( *cyLogical* / *cyHimetric*) X tamaño de fuente  
  
 La versión sin parámetros devuelve un identificador a una fuente de tamaño correcto para la pantalla.  
  
##  <a name="initializefont"></a>  CFontHolder::InitializeFont  
 Inicializa un `CFontHolder` objeto.  
  
```  
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,  
    LPDISPATCH pFontDispAmbient = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pFontDesc*  
 Puntero a una estructura de descripción de la fuente ( [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782)) que especifica las características de la fuente.  
  
 *pFontDispAmbient*  
 Puntero a la propiedad fuente de ambiente del contenedor.  
  
### <a name="remarks"></a>Comentarios  
 Si *pFontDispAmbient* no es NULL, el `CFontHolder` objeto está conectado a un clon de la `IFont` interfaz utilizada por la propiedad fuente de ambiente del contenedor.  
  
 Si *pFontDispAmbient* es NULL, una nueva fuente de objeto se crea desde la que apunta la descripción de la fuente *pFontDesc* o, si *pFontDesc* es NULL, un valor predeterminado Descripción.  
  
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
 *lptm*  
 Un puntero a un [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) estructura que recibirá la información.  
  
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
 *pDC*  
 Contexto de dispositivo en el que se selecciona la fuente.  
  
 *cyLogical*  
 Alto, en unidades lógicas, del rectángulo en el que se dibuja el control.  
  
 *cyHimetric*  
 Alto, en unidades MM_HIMETRIC, del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la fuente que se va a reemplazar.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [GetFontHandle](#getfonthandle) para obtener información sobre la *cyLogical* y *cyHimetric* parámetros.  
  
##  <a name="setfont"></a>  CFontHolder::SetFont  
 Libera cualquier fuente existente y se conecta el `CFontHolder` objeto a un `IFont` interfaz.  
  
```  
void SetFont(LPFONT pNewFont);
```  
  
### <a name="parameters"></a>Parámetros  
 *pNewFont*  
 Puntero a la nueva `IFont` interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPropExchange (clase)](../../mfc/reference/cpropexchange-class.md)
